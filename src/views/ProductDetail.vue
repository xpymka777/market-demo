<template>
  <h1>Product Detail</h1>
  <div class="product">
    <div class="product-image">
      <img :src="selectedProduct.thumbnail" alt="product-image">
    </div>
    <div class="product-details">
      <p>Brand: {{selectedProduct.brand}}</p>
      <p>Description: {{selectedProduct.description}}</p>
      <h2>Price: ${{selectedProduct.price}}</h2>
    </div>
  </div>
  <button @click="router.push({name:'Catalog'})">Back to catalog</button>
</template>

<script>
import {defineComponent} from "vue";
export default defineComponent({
  name:'ProductDetails'
})

</script>

<script setup>

import {computed} from "vue";
import {productsStore} from "@/stores/products";
import {useRoute, useRouter} from "vue-router";

const store = productsStore();
const route = useRoute();
const  router = useRouter();

const selectedProduct = computed(() => {
  return store.products.find((item) => item.id === Number(route.params.id));
})

</script>

<style scoped>
.product{
  display: flex;
  margin-top: 50px;
}
.product-image{
  margin-right: 24px;
}
</style>