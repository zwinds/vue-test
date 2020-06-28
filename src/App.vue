<template>
<div>
  <h1>hello {{title}}!</h1>
  <ul>
    <li v-for="(good,index) in goods">
      {{index}}:
      {{good.text}}

      |

      {{good.price}}
      <el-button type="primary" icon="el-icon-plus" @click="addCart(index)" circle></el-button>
    </li>
  </ul>
  <table border="1">
    <tr>
    <td>商品</td>
    <td>单价</td>
    <td>价格</td>
    <td>数量</td>
    <td>操作</td>
    </tr> 
    <tr>
      <tr v-for="c in cart">
        <td>{{c.text}}</td>
        <td>{{c.price}}</td>
        <td>{{c.price * c.count}}</td>
        <td>{{c.count}}</td>
    </tr>
  </table>
</div>
</template>

<script>
import Vue from 'vue';
import { Button } from 'element-ui';
Vue.use(Button);
export default {
  data(){
    return {
      title:'vue test',
      goods:[
        {text:"苹果",price:80},
        {text:"香蕉",price:100},
        {text:"西瓜",price:60},
        {text:"芒果",price:120},
      ],
      cart:[]
    }
  },
    methods:{
    addCart(i){
      console.log( '添加购物车' )
      let item = this.goods[i]
      let good = this.cart.find(v=>v.text==item.text)
      if (good){
        good.count  +=  1
      }else{
        this.cart.push({...item, count:1})
      }
    }
  }
}
</script>

<style>
h1{
  color: blue;
}
</style>