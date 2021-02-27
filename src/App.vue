<template>
  <div id="app">
    <input type="text" v-model="inputText">
    <button @click="convert">住所自動入力</button>
    <p>Address　:　{{Address}}</p>
  </div>  
</template>

<script>
import axios from "axios";
export default {
  data () {
    return {
      inputText: "",
      Address: "",
    };
  },
   methods: {
     async convert() {
      const item = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.inputText}?apiKey=UuqgYKMuxKCuqFJFGBEBFPkZmIMxGV4bBdBetew`);
      console.log(item)
      this.Address = item.data.allAddress
    }
  }
}
</script>

