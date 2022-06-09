<script>
	export let name;
	import {onMount} from 'svelte';
	let footprint; onMount();
	async function getData() {
       const response = await fetch(
            'https://icanhazdadjoke.com/',
            {
                method: 'GET',
                headers: {
                    'Accept': 'application/json'
                },
            }
        );
        const data = await response.json();
        console.log(data);
        footprint = data?.joke;
    }
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<p>This is an example of a Svelte app with an api call.</p>
	<div>
    <button on:click={getData}>Get Joke</button>
    <div>
    {#if footprint}
        <h2>{footprint}</h2>
    {:else}
        <p>Click the Button</p>
    {/if}
	</div>
	<p>Thanks to <a href="https://c653labs.com/">C653 Labs</a> for the <a href="https://icanhazdadjoke.com/">Dad Jokes</a></p>
</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>