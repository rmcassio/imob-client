<script lang='ts'>
	export let data;

	let currentCategory = 'Comprar';
	let items = data.items;

    function changeCategory(newCategory: string) {
        currentCategory = newCategory;
		filterItems();
		return;
    }

	 function filterItems() {
		return items = data.items.filter(item => {
			return item.type == currentCategory;
		})

	}

	filterItems();
</script>

<section class="bg-white dark:bg-gray-900">
	<div class="container px-6 py-10 mx-auto">
		<h1
			class="text-2xl font-semibold text-center text-gray-800 capitalize lg:text-3xl dark:text-white"
		>
			Ligue já!
		</h1>
		<div
			class="flex py-4 mt-4 overflow-x-auto overflow-y-hidden justify-center dark:border-gray-700"
		>
			{#each data.categories as category}
				{#if currentCategory === category}
					<button
						class="h-12 px-8 py-2 -mb-px text-sm text-center text-blue-600 bg-transparent border-b-2 border-blue-500 sm:text-base dark:border-blue-400 dark:text-blue-300 whitespace-nowrap focus:outline-none"
					>
						{category}
					</button>
				{:else}
					<button
                        on:click={()=>{changeCategory(category)}}
						class="h-12 px-8 py-2 -mb-px text-sm text-center text-gray-700 bg-transparent border-b-2 border-gray-200 sm:text-base dark:text-white whitespace-nowrap cursor-base focus:outline-none dark:border-gray-700 dark:hover:border-gray-400 hover:border-gray-400"
					>
						{category}
					</button>
				{/if}
			{/each}
		</div>

		{#each items as { city, description, imageUrl }}
			<section class="lg:flex lg:items-center">
				<br />
				<br />
				<div class="lg:w-1/2">
					<p class="text-lg tracking-wider text-blue-500 uppercase dark:text-blue-400">{city}</p>
					<h2 class="mt-2 text-2xl font-semibold text-gray-800 capitalize dark:text-white">
						{description}
					</h2>
				</div>

				<div class="mt-4 lg:w-1/2 lg:mt-0">
					<img class="object-cover w-full h-64 rounded-lg md:h-96" src={imageUrl} alt="" />
				</div>
				<br />
			</section>
		{/each}
	</div>
</section>
