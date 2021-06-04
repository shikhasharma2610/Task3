<template>
  <div>
  <img :src="picture" :class="gender">
  <h1>{{firstname}}{{lastname}}</h1>
  <h3>Email:{{email}}</h3>
  <button :class="gender" @click="getuser()">Get Random User</button></div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      firstname:"John",
      lastname:"Deo",
      email:"john@gmail.com",
      gender:"male",
      picture:"https://randomuser.me/api/portraits/men/10.jpg"
    }
  },
  methods:{
    getdata(data){
      this.picture=data.results[0].picture.large
      setTimeout(()=>{
      this.firstname=data.results[0].name.first
      this.lastname=data.results[0].name.lastname
      
      this.email=data.results[0].email
      this.gender=data.results[0].gender
    },200)
    },
    getuser(){
      fetch('https://randomuser.me/api')
      .then(response=> response.json())
      .then(data=> this.getdata(data));
      
    }
    
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 400px;
  height: 100vh;
  margin:auto;
  text-align: center;
  align-items:center;
  justify-content: center;
}
img{
  border-radius: 50%;
  border: 5px #333 solid;
  margin-bottom: 1rem;
}
h1,
h3 {
  margin-bottom: 1rem;
  font-weight: normal;
}
button{
  cursor: pointer;
  display: inline-block;
  background: #333;
  color: white;
  font-size: 18px;
  border: 0;
  padding: 1rem 1.5rem;
}
button:focus {
  outline: none;
}
button:hover {
  transform: scale(0.98);
}
.male {
  border-color: steelblue;
  background-color: steelblue;
}

.female {
  border-color: pink;
  background-color: pink;
  color: #333;
}
</style>
