<template>
    <el-config-provider namespace="ep">
        <el-input
            v-model="textarea"
            :rows="2"
            type="textarea"
            placeholder="Please input"
        />
    </el-config-provider>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { record } from 'rrweb';

const textarea = ref();

let events = [];
const onStart = () => {
    // 清空 events
    events = [];
    record({
        emit(event) {
            events.push(event);
        },
    });
};

onMounted(() => onStart());
</script>

<style>
#app {
    text-align: center;
    color: var(--ep-text-color-primary);
}

.element-plus-logo {
    width: 50%;
}
</style>
