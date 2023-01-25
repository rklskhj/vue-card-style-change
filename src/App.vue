<template>
  <div class="layout">
    <div class="list-wrap">
      <div class="title">
        <h1>신상품</h1>
        <p>새로운 상품을 만나보세요</p>
      </div>
      <div class="list" :style="gridStyle">
        <div class="list__box" v-for="(product, i) in products" :key="i">
          <img class="image" :src="products[i].image" />
          <p
            class="brand"
            :style="{
              color: colors.hex,
              fontSize: fontChange.fontSize + 'px',
            }"
          >
            {{ products[i].brand }}
          </p>
          <h4>{{ products[i].title }}</h4>
          <p class="contents">{{ products[i].contents }}</p>
          <h3 class="price">{{ products[i].price }}원</h3>
        </div>
      </div>
    </div>
    <div class="change-list">
      <div class="inputBox1">
        <h4>컬럼수</h4>
        <input type="text" v-model="culumnCount" />
      </div>
      <div class="inputBox2">
        <h4>브랜드명</h4>
        <div class="inputBox1">
          <span>글씨크기</span>
          <input type="text" v-model="fontChange.fontSize" />
        </div>
        <div class="inputBox1">
          <span>글씨색상</span>
          <input type="text" v-model="colors.hex" />
        </div>
        <div class="inputBox1"><Chrome v-model="colors"></Chrome></div>
      </div>
    </div>
  </div>
</template>

<script>
import products from "./assets/products";
import { Chrome } from "@ckpack/vue-color";

import "@/assets/global.css";

export default {
  name: "App",
  components: {
    Chrome,
  },
  data() {
    return {
      products: products,
      culumnCount: 4,
      discount: "",
      fontChange: {
        fontSize: "",
      },
      colors: {
        hex: "#194d33",
        hex8: "#194D33A8",
        hsl: { h: 150, s: 0.5, l: 0.2, a: 1 },
        hsv: { h: 150, s: 0.66, v: 0.3, a: 1 },
        rgba: { r: 25, g: 77, b: 51, a: 1 },
        a: 1,
      },
    };
  },
  computed: {
    gridStyle() {
      return { gridTemplateColumns: `repeat(${this.culumnCount}, 1fr)` };
    },
  },
};
</script>

<style>
.layout {
  display: flex;
  justify-content: center;
  width: 100%;
  min-height: 50rem;
  background-color: gainsboro;
}
.list-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 80rem;
  height: 100%;
  margin: 2rem 2rem;
  padding: 10px;
  background-color: white;
}

.title {
  text-align: center;
  margin-top: 2rem;
  margin-bottom: 8rem;
}
.list {
  display: grid;
  justify-items: center;
  width: 100%;
  gap: 1rem;
}
.image {
  border: 1px solid gainsboro;
  border-radius: 4px;
  width: 15rem;
  object-fit: cover;
}
.brand {
  color: grey;
  font-weight: bold;
  font-size: small;
}
.contents {
  color: grey;
  font-weight: bold;
  font-size: smaller;
  margin: 5px 0;
}
.change-list {
  display: flex;
  flex-direction: column;
  background-color: white;
  gap: 1.2rem;
  margin: 2rem 0;
  padding: 15px 20px;
  width: 16rem;
}
.inputBox1 {
  display: flex;
  justify-content: space-between;
  margin: 5px 0;
}

.inputBox2 {
  display: flex;
  flex-direction: column;
}

input[type="text"] {
  width: 8rem;
}
</style>
