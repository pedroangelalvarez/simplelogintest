<script>
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	import { v4 as uuidv4 } from 'uuid'; 
	let isLoading = false;
	let username = '';
	let password = '';
	const usernameId = uuidv4();
	const passwordId = uuidv4();
	function handleSubmit() {  
		if (username === '' || password === '') {
			alert('Error: Ingrese un usuario y contraseña');
			return;
		}
		else{
			isLoading = true;
			let tiempoEspera = Math.floor(Math.random() * 5) + 3;
			setTimeout(() => {
				isLoading = false;
				window.location.href = "/home";
			}, tiempoEspera*1000);
		}             
	}

	function handleGoogleLogin() {
    isLoading = true;
	let tiempoEspera = Math.floor(Math.random() * 5) + 3;
    setTimeout(() => {
      isLoading = false;
	  window.location.href = "/home";
    }, tiempoEspera*1000);
  }


</script>

<svelte:head>
	<title>Simple Login Test</title>
	<meta name="Login to Testing" content="QA" />
</svelte:head>

<section>
	<div class="mainView">
		{#if isLoading}
		<div class="skeleton">
		  <div class="skeleton__avatar"></div>
		  <div class="skeleton__author"></div>
		  <div class="skeleton__details"></div>
		</div>
		{:else}
		<div class="titleContainer">
		  <h1>Iniciar sesión</h1>
		</div>
		<form on:submit="{handleSubmit}">
		  <label for="{usernameId}">Usuario:
			<input type="text" id="{usernameId}" bind:value="{username}" />
		  </label>
		  <label for="{passwordId}">Contraseña:
			<input type="password" id="{passwordId}" bind:value="{password}" />
		  </label>
		<button type="submit">Iniciar sesión</button>
		<p>o</p>
  <button class="google-button" on:click="{handleGoogleLogin}">
  <span class="google-icon" aria-hidden="true"></span>
  <span class="google-text">Iniciar sesión con Google</span>
  </button>
		</form>
		{/if}
		</div>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.mainView{
  position: fixed;
  background: linear-gradient(45deg, #AA1090, #a19043);
  top: 0;
  left: 0;
  height:100%;
  width:100%;
  text-align: center;
  animation: gradientAnimation 10s ease alternate infinite;
}

@keyframes gradientAnimation {
  0% {
    background-position: 0% 50%;
  }
  100% {
    background-position: 100% 50%;
  }
}
.titleContainer{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 5vh;
}
h1 {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 20px;
}

form {
  max-width: 300px;
  margin: 0 auto;
}

label {
  display: block;
  margin-bottom: 10px;
  font-weight: bold;
}

input[type="text"],
input[type="password"] {
  width: 100%;
  padding: 8px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 15px;
}

button[type="submit"] {
  background-color: #4caf50;
  color: #fff;
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
}

button[type="submit"]:hover {
  background-color: #45a049;
}

.google-button {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #fff;
  color: #757575;
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 10px 30px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.google-button:hover {
  background-color: #f1f1f1;
}

.google-icon {
  display: inline-block;
  width: 20px;
  height: 20px;
  margin-right: 10px;
  background-image: url("https://www.svgrepo.com/show/303108/google-icon-logo.svg");
  background-repeat: no-repeat;
  background-size: cover;
}

.google-text {
  font-weight: bold;
}
.skeleton__avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background-color: #ddd;
  margin: 0 auto;
  margin-bottom: 20px;
  animation: skeleton-loading 1s ease-in-out infinite;
}
@keyframes skeleton-loading {
  0% {
	background-color: #ddd;
  }
  50% {
	background-color: #ccc;
  }
  100% {
	background-color: #ddd;
  }
}
.skeleton__author {
  width: 60%;
  height: 20px;
  background-color: #ddd;
  margin: 0 auto;
  margin-bottom: 20px;
  animation: skeleton-loading 1s ease-in-out infinite;
}
.skeleton__details {
  width: 80%;
  height: 20px;
  background-color: #ddd;
  margin: 0 auto;
  margin-bottom: 20px;
  animation: skeleton-loading 1s ease-in-out infinite;
} 
</style>
