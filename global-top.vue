<script setup lang="ts">
import { ref, onMounted } from 'vue'

const start = Date.now()
const elapsed = ref('00:00')

onMounted(() => {
	setInterval(() => {
		const diff = Math.floor((Date.now() - start) / 1000)
		const mins = String(Math.floor(diff / 60)).padStart(2, '0')
		const secs = String(diff % 60).padStart(2, '0')
		elapsed.value = `${mins}:${secs}`
	}, 1000)

	console.log('Timer started')

})
</script>

<template>
	<div v-if="$nav.currentPage >= 4 && $nav.currentPage <= 20" class="timer">
		<div class="fixed bottom-3 left-6 z-50 text-sm font-mono">
			Vagelis Papaioannou
		</div>
		<div class="fixed bottom-3 right-6 z-50 text-sm font-mono">
			{{ elapsed }}
		</div>
	</div>
</template>