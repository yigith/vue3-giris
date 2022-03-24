<script>
export default {
  data() {
    return {
      message: "Hello world!",
      alinacaklar: ["patates", "domates"],
      urun: "",
      goster: false,
      acikMi: false
    }
  },
  methods: {
    ekle(event) {
      event.preventDefault();
      this.alinacaklar.push(this.urun);
      this.urun = "";
    },
    sil(indeks, event) {
      event.preventDefault();
      this.alinacaklar.splice(indeks, 1);
    }
  },
  computed: {
    lambaAcmaKapamaMetni: function() {
      return this.acikMi ? "LAMBAYI KAPAT" : "LAMBAYI AÇ";
    }
  }
}
</script>

<template>
<h1>Vue Öğreniyorum</h1>
Your message: <input type="text" v-model="message" />
<h2>{{ message }} {{ message }} {{ message }}</h2>

<hr />

<h2>Alışveriş Listem</h2>
<form @submit="ekle">
  Alınacak: <input type="text" v-model="urun" required /> 
  <button>Ekle</button>
</form>

<ul>
  <li v-for="(alinacak, i) in alinacaklar">
    {{ alinacak }}
    <a href="#" @click="sil(i, $event)">&times</a>
  </li>
</ul>

<hr />

<input type="checkbox" v-model="goster" /> Aşağıdaki paragrafı göster

<p v-if="goster">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Cum quo incidunt libero blanditiis corporis rem asperiores fugiat, aliquid laudantium ut saepe nemo laboriosam sed rerum dicta, nostrum nisi perferendis quos.</p>

<hr />

<button @click="acikMi = !acikMi">
  {{ lambaAcmaKapamaMetni }}
</button>

<div>
  <img v-if="acikMi" src="./assets/img/on.png" alt="Açık Lamba" width="100">
  <img v-else src="./assets/img/off.png" alt="Açık Lamba" width="100">
</div>
</template>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;
}
</style>
