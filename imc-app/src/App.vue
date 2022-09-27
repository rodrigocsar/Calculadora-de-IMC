<template>
  <h1 class="label-title">Calculo do IMC</h1>
  <h2 class="label-subtitle">Digite seu peso e altura para calcular seu IMC</h2>

  <div class="div-imc">
    <span class="p-float-label">
      <InputText
        id="input-weigth"
        type="text"
        v-model="weight"
        :disabled="imc"
      />
      <label for="input-weight">Peso</label>
    </span>
  </div>

  <div class="div-imc">
    <span class="p-float-label">
      <InputText
        id="input-heigth"
        type="text"
        v-model="heigth"
        :disabled="imc"
      />
      <label for="input-height">Altura</label>
    </span>
  </div>

  <div class="div-imc" v-if="!imc">
    <Button label="Limpar" @click="clear" />
    <Button label="Calcular" @click="calculate" class="button-calculate" />
  </div>

  <div v-if="imc">
    <p class="label-result">Seu IMC e :{{ imc }}</p>
    <p class="label-classification">
      Classificaçao do seu IMC : {{ classification }}
    </p>
    <Button @click="clear" label="Calcular novvamente " />
  </div>
</template>

<script>
export default {
  data() {
    return {
      heigth: null,
      weight: null,
      imc: null,
      classification: "",
    };
  },
  methods: {
    calculate: function () {
      this.heigth;
      this.weight;
      this.imc = (this.weight / (this.heigth * this.heigth)).toFixed(2);
      if (this.imc < 18.5) {
        this.classification = "Abaixo";
      } else if (this.imc >= 18.5 && this.imc < 25) {
        this.classification = "Normal";
      } else if (this.imc >= 25 && this.imc < 30) {
        this.classification = "Obesidade";
      } else {
        this.classification = "Obesidade morbida";
      }
    },
    clear() {
      this.heigth = null;
      this.weight = null;
      this.imc = null;
      this.result = "";
      this.classification = "";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.div-imc {
  margin-top: 2rem;
}
.button-calculate {
  margin-left: 1rem !important;
}
.label-title {
  font-size: 2rem;
}
.label.subtitle {
  font-size: 1.1rem;
}
.label-result {
  font-size: 1.5rem;
}
.label-classification {
  font-size: 1.5rem;
}
</style>
