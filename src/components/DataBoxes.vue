<template>
	<div class="grid md:grid-cols-2 gap-4">
		<!-- Box 1 -->

		<div class="shadow-md bg-blue-100 p-10 text-center rounded">
			<h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
			<div class="text-2xl mb-4">
				<span class="font-bold">New:</span>
				{{ numberWithCommas(stats.NewConfirmed) }}
			</div>
			<div class="text-2xl mb-4">
				<span class="font-bold">Total:</span>
				{{ numberWithCommas(stats.TotalConfirmed) }}
			</div>
		</div>

		<!-- Box 2 -->
		<div class="shadow-md bg-red-200 p-10 text-center rounded">
			<h3 class="text-3xl text-red-600 font-bold mb-4">Deaths</h3>
			<div class="text-2xl mb-4">
				<span class="font-bold">New:</span>
				{{ numberWithCommas(stats.NewDeaths) }}
			</div>
			<div class="text-2xl mb-4">
				<span class="font-bold">Total:</span>
				{{ numberWithCommas(stats.TotalDeaths) }}
			</div>
		</div>
		<!-- Box 3 -->
		<div class="shadow-md bg-green-200 p-10 text-center rounded mt-4">
			<h3 class="text-3xl text-green-600 font-bold mb-4">Recoveries</h3>
			<div class="text-2xl mb-4">
				<span class="font-bold">New:</span>
				{{ numberWithCommas(stats.NewRecovered) }}
			</div>
			<div class="text-2xl mb-4">
				<span class="font-bold">Total:</span>
				{{ numberWithCommas(stats.TotalRecovered) }}
			</div>
		</div>

		<div class="shadow-md bg-yellow-200 p-10 text-center rounded mt-4">
			<h3 class="text-3xl text-yellow-600 font-bold mb-4">
				Active Cases
			</h3>
			<div class="text-2xl mb-4">
				<span class="font-bold">New:</span>
				{{
					numberWithCommas(
						stats.NewConfirmed -
							stats.NewDeaths -
							stats.NewRecovered
					)
				}}
			</div>
			<div class="text-2xl mb-4">
				<span class="font-bold">Total:</span>
				{{
					numberWithCommas(
						stats.TotalConfirmed -
							stats.TotalDeaths -
							stats.TotalRecovered
					)
				}}
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'DataBoxes',
	props: ['stats'],
	methods: {
		numberWithCommas(x) {
			return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
		},
	},
};
</script>
