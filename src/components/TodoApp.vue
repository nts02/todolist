<template>
  <div class="container">
    <h2 class="text-center mt-5">Todo List</h2>

    <!-- Input  -->
    <div class="d-flex">
      <input v-model="task" type="text" placeholder="Enter task" class="form-control">
      <button @click="submitTask"  class="btn btn-warning rounded-0">Submit</button>
    </div>

    <!-- Task table -->
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Name</th>
          <th scope="col">#</th>
          <th scope="col">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task,index) in tasks" :key="index">
          <th scope="row">{{task.id}}</th>
          <td>{{task.name}}</td>
          
          <td>
            <div class="text-center" @click="editTask(index)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center" @click="deleteTask(index)">
              <span class="fa fa-trash"></span>
            </div> 
          </td>
        </tr>
       
      </tbody>
  </table>
  </div>
</template>
<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      task : '',
      editedTask:null,
      tasks : [
        {
          id : 1,
          name : 'Mark',
          
        },
        {
          id : 2,
          name : 'NTS',
        }
      ]
    }
  },
  methods : {
    submitTask() {
      if(this.task.length == 0) return ;
      if(this.editedTask === null) {
        this.tasks.push({
          id :  this.tasks.length + 1,
          name : this.task,
        })
      }else {
        this.task[this.editedTask].name = this.task;
        this.editedTask = null;
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1)
    },
    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
