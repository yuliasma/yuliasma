<template>
  <div class="container">
    <h1>To-Do List</h1>
    <div class="todo-form">
      <input v-model="newTask" placeholder="Add a new task" />
      <button @click="addTask">Add</button>
    </div>
    <div class="todo-list">
      <div v-for="(task, index) in tasks" :key="index" class="todo-item">
        <input type="checkbox" v-model="task.completed" />
        <span :class="{ completed: task.completed }">{{ task.text }}</span>
        <button @click="deleteTask(index)">Delete</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({
          text: this.newTask,
          completed: false,
        });
        this.newTask = '';
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
.container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.todo-form {
  display: flex;
  margin-bottom: 10px;
}

.todo-form input {
  flex-grow: 1;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.todo-form button {
  margin-left: 10px;
  padding: 5px 10px;
  background-color: #4f46e5;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.todo-list .todo-item {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.todo-list .todo-item input[type="checkbox"] {
  margin-right: 10px;
}

.todo-list .todo-item .completed {
  text-decoration: line-through;
  color: #888;
}

.todo-list .todo-item button {
  margin-left: 10px;
  padding: 5px 10px;
  background-color: #e54f4f;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
