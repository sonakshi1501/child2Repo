<template>
  <v-app>
    <v-main>
<v-container>
  <v-row>
    <v-col>
      <h1>Github User Api</h1>
    </v-col>
  </v-row>
  <v-row v-if="!users.length>0">
    <v-col class="text-center">
      <v-progress-circular
      :size="70"
      :width="7"
      color="primary"
      indeterminate
    ></v-progress-circular>
    </v-col>
  </v-row>
  <v-row v-else>
    <v-col md="3" v-for="(item,index) in users" :key="index">
      <v-card
    class="mx-auto"
    max-width="400"
  >
    <v-img
      class="white--text align-end"
      height="200px"
      :src="item.avatar_url"
      cover
    >
    </v-img>
      <v-card-title class="mb-0">{{item.login}}</v-card-title>


    <v-card-actions>
      <v-btn
        color="orange"
        variant="text"
        :href="item.html_url"
        target="_blank"
      >
      Github Profile
      </v-btn>
    </v-card-actions>
  </v-card>
    </v-col>
  </v-row>
</v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      users:[]
    }
    
  },
  mounted(){
    this.getData()
  },
  methods:{
    getData(){
      fetch("https://api.github.com/users").then(res=>res.json()).then(data=>{
      this.users=data

      }).catch(e=>{console.log(e)})
    }
  }
};
</script>
