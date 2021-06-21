<template>
  <div>
    <div>
      <h1 class="title">Lista de dados json</h1>
    </div>
    <div class="card">
      <ul v-for="user in users" :key="user.id" class="card-container">
        <li class="card-item">
          <p>{{ user.name }}</p>
          <p>{{ user.email }}</p>
          <p>{{ user.phone }}</p>

          <!-- aqui esta vindo uma imagem so pelo array posição zero -->
          <!-- <img :src="user.photos[0].thumbnailUrl" /> -->

          <!-- O user.photos tem um array com 2 images, aqui eu fiz um outro loop pegando o user.photos com 2 posições, 
          e fiz um loop, puxando assim todas as imagem dentro do array -->
          <div v-for="photoUrl in user.photos" :key="photoUrl.id">
            <img :src="photoUrl.thumbnailUrl" />
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import users from "./users.json";

export default {
  data() {
    return {
      users,
    };
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  border: 0;
}

.title {
  margin-bottom: 25px;
}

.card {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.card-container {
  width: 33%;
  display: flex;
  align-items: center;
}

.card-item {
  width: 100%;
  padding: 25px;
  list-style: none;
  border: 1px solid rgb(238, 238, 238);
}

.card-item p {
  padding: 8px;
}
</style>
