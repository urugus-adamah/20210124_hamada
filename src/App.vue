<template>
  <div id="app">
    <input type="text" v-model="postnumber">
    <button @click="getAddress()">住所自動入力</button>
    <p>Address:{{address}}</p>
  </div>
    
</template>
<script>
import axios from "axios";
export default {
  data(){
    return{
      postnumber:"",
      address:""
    };
  },
  methods:{
    async getAddress(){
      const key = "eBf0Hooj6sbaPH2g6i64EInrJQerRsE7nkpQPPF";

      const item = await axios.get('https://apis.postcode-jp.com/api/v4/postcodes/'+this.postnumber+'/?apikey='+key);

      this.address = item.data[0].allAddress;
    }
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
