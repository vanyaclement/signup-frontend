<template>
 
  <v-app>
    <div class="bg">
    <v-main class="d-flex justify-center align-center">
      <v-col cols="10" lg="4">
        <v-card class="pa-4">
          
         <v-card-title class="text-center">Sign Up</v-card-title>
        
          <v-form fast-fail @submit.prevent>

            <v-card-title>First Name</v-card-title>

      <v-text-field v-model="firstName" type="text" placeholder="First name" :rules="firstNameRules"></v-text-field>
   
     
      <v-card-title>Last Name</v-card-title>
      <v-text-field v-model="lastName" type="text" placeholder="Last name" :rules="lastNameRules" ></v-text-field>


      <v-card-title>Email</v-card-title>
      <v-text-field v-model="email" type="email" placeholder="Email" :rules="emailRules" ></v-text-field>

      <v-card-title>Password</v-card-title>
      <v-text-field v-model="password" type="password" placeholder="Password" :rules="passwordRules" ></v-text-field>

      <v-btn type="submit" block class="mt-2" color="blue" @click="saveData">SIGN UP</v-btn>
      
      </v-form>
        </v-card>

      </v-col>
    </v-main>
  </div>
  </v-app>

</template>

<script>
import axios from 'axios';

export default {
  name: "App",


  

  data: () => ({
    firstName: '',
      firstNameRules: [
        v => /^[a-zA-Z]+$/.test(v) || 'Enter a valid First Name',
      ],
      lastName: '',
      lastNameRules: [
        v => /^[a-zA-Z]+$/.test(v) || 'Enter a valid Last Name',
  ],
  email: '',
  emailRules: [
    v => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(v) || 'Enter a valid Email'
  ],
  password:'',
      passwordRules:[
          v => v.length >=8 || 'Minimum length is 8 char,',
          v => /[A-Z]/.test(v) || 'Password must contain one upper Case Letter.',
          v => /[a-z]/.test(v) || 'Password must contain a lower case letter.',
          v => /[0-9]/.test(v) || 'Password must contain a number',
          v => /[^A-Za-z0-9]/.test(v) || 'Password must contain special character'
        ]
  }),
  created(){

  },
  mounted(){
    console.log("mounted() called.........");

  },
  methods:{
    async saveData()
    {
     await axios.post("http://localhost:5100/user/create", this.student)
      .then((data)=> {
        console.log(data,"asbchbdhbhjsdbchj")
      })
       .catch((error) => {
        console.log(error,"occuresddd")
       });
      
    }
  }
 
}

</script>
<style scoped>
.bg{
  background-color: blue;
}
</style>
