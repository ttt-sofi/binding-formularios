<template>
  <form>
    <div>
      <label>Título de la tarjeta: </label>
      <input v-model="tarjeta.titulo"/>
    </div>

    <div>
      <label>Chip SRC: </label>
      <input  v-model="tarjeta.chipSRC"/>
    </div>

    <div>
      <label>Número: </label>
      <input type="number" v-model="tarjeta.numero"/>
    </div>

    <div>
      <label>Fecha de expiración: </label>
      <input  v-model="tarjeta.fecha" />
    </div>

    <div>
      <label>Propietario: </label>
      <input type="text" v-model="tarjeta.propietario" />
    </div>

    <div>
      <label>Tipo de tarjeta SRC: </label>
      <input v-model="tarjeta.tipoSRC"/>
    </div>
  </form>

  <div class="carnet">
    <h3>{{ tarjeta.titulo }}</h3>
    <img width="40" :src="tarjeta.chipSRC" alt="" />
    <div>
      <h2>{{tarjeta.numero}}</h2>
      <span>Fecha Exp: <b>{{fechaFormateada}}</b></span>
    </div>
    <footer>
      <span>{{tarjeta.propietario}}</span>
      <img  width="60" :src="tarjeta.tipoSRC"/>
    </footer>
  </div>
</template>

<script>

export default {
  name: "App",
  data() {
    return {
      tarjeta: {
        titulo: "Tarjeta de Credito",
        numero: "1234 5678 9012 3456",
        fecha: "01/30",
        propietario: "William Henry Gates III",
        chipSRC:"/src/assets/img/chip.png",
        tipoSRC:"/src/assets/img/visa.png"
      },
    };
  },
  computed: {
    // Computed property para formatear la fecha
    fechaFormateada() {
      if (!this.tarjeta.fecha) return ''; // Verificar si hay una fecha ingresada

      // Crear un objeto Date a partir de la fecha seleccionada
      const fecha = new Date(this.tarjeta.fecha);
      
      // Obtener el mes y el día
      const mes = String(fecha.getMonth() + 1).padStart(2, '0'); // Los meses son 0-indexados en JS
      const dia = String(fecha.getDate()).padStart(2, '0'); // Agrega un '0' al principio si es necesario

      // Devolver el formato MM/DD
      return `${mes}/${dia}`;
    }
  }
};

</script>

<style>
* {
  margin: 0;
}
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60vh;
  font-size: 10px;
  font-family: sans-serif;
}

#app {
  display: flex;
  gap: 40px;
}
form {
  padding: 18px;
  border-radius: 20px;
  border: ridge 1px;
  box-shadow: 1px 1px 1px 1px gray;
  font-weight: bold;
  display: flex;
  flex-direction: column;
  gap: 15px;
  justify-content: center;
}
form div {
  display: grid;
  grid-template-columns: 100px 200px;
  align-items: center;
  gap: 5px;
}

form div label {
  text-align: right;
}

.carnet {
  width: 400px;
  height: 230px;
  background: #1c1a1e;
  color: white;
  border-radius: 20px;
  padding: 20px;
  box-shadow: 0px 0px 10px 2px black;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

h3 {
  font-size: 20px;
}

h2 {
  font-size: 30px;
  letter-spacing: 10px;
  margin-bottom: 15px;
  text-shadow: 0px 0px 1px gold;
  font-family: Times;
}

b {
  font-size: 16px;
}

footer {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  font-weight: bold;
  font-size: 18px;
  text-transform: uppercase;
  font-style: italic;
}
</style>
