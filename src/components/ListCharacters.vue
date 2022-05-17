<template>
  <section>
    <div class="characters">
            <h2>Character List</h2>
        <div class="characters_item" v-for="character in characters" :key="character.id">
                      
            <CardCharacter :character="character"/>
                     
        </div>
    </div>
  </section>
</template>

<script>
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'
import CardCharacter from '@/components/CardCharacter.vue'

export default {
    components: {
        CardCharacter 
    },
    setup() {
        const store = useStore();
        const characters = computed(() => {
            return store.state.charactersFilter;
        });
        onMounted(() => {
            store.dispatch("getCharacters");
        });
        return {
            characters
        }
    }
}
</script>

<style>


</style>