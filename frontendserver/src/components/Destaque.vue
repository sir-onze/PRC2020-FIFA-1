<template>
  <div :style="{backgroundColor:'#031927',width:'100%',marginRight:'10vh',marginLeft:'-0.2%'}">
          <h1 :style="{color:'white',marginLeft:'5vh',marginTop:'5vh'}">Em Destaque</h1>
          <table>
                <th>
               <div :style="{backgroundColor:'black',width:'100%',height:'2%'}"></div>
                <Ouro  v-bind:player ="this.player1" :style="{width:'100%',marginLeft:'33.33%',marginTop:'12vh'}"/>
                </th>
                <th>
                <div :style="{backgroundColor:'black',width:'100%',height:'2%'}"></div>
                <Ouro  v-bind:player ="this.player2" :style="{width:'100%',marginLeft:'33.33%',marginTop:'12vh'}"/>
                </th>
                <th>
                <div :style="{backgroundColor:'black',width:'100%',height:'2%'}"></div>
                <Ouro  v-bind:player ="this.player3" :style="{width:'100%',marginLeft:'33.33%',marginTop:'12vh'}"/>
                </th>
          </table>
        </div>
</template>

<script>
/*Neste momentos os items estão fixos assim como os valores dos atributos nomes e etc das cartas
que nas proximas versoes vao ter de ser passados como params para as cartas 
*/
import Ouro from './CartaOuro';
import axios from "axios";
  export default {
    props: {
      source: String,
    },
     data: () => ({
      drawer: null,
      player1: [],
      player2: [],
      player3: []
    }),
     mounted: function() {
    const url = "http://localhost:5011/players/card/Ronaldo-Normal";
    let config = {
      headers: {
        Authorization: "Bearer " + this.getToken
      }
    };
    axios.get(url, config).then(res => {
      this.player1 = res.data;
      console.log(this.player1)
    });

    const url2 = "http://localhost:5011/players/card/Neymar-Normal";
  
    axios.get(url2, config).then(res => {
      this.player2 = res.data;
      console.log(this.player2)
    });

    const url3 = "http://localhost:5011/players/card/Pepe-Normal";
  
    axios.get(url3, config).then(res => {
      this.player3 = res.data;
      console.log(this.player3)
    });
  },
    components: {
        Ouro,
  },
  }
</script>
