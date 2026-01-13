<script setup>
const props = defineProps({
  editingSubscription: {
    type: Object,
    required: true
  }
});
</script>

<template>
  <!-- 订阅名称 -->
  <div>
    <label for="sub-edit-name" class="block text-sm font-medium text-gray-700 dark:text-gray-300">订阅名称</label>
    <input type="text" id="sub-edit-name" v-model="editingSubscription.name" placeholder="（可选）不填将自动获取"
      class="mt-1 block w-full px-3 py-2 bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-600 rounded-md shadow-xs focus:outline-hidden focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm dark:text-white">
  </div>

  <!-- 订阅链接 -->
  <div>
    <label for="sub-edit-url" class="block text-sm font-medium text-gray-700 dark:text-gray-300">订阅链接</label>
    <input type="text" id="sub-edit-url" v-model="editingSubscription.url" placeholder="https://..."
      class="mt-1 block w-full px-3 py-2 bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-600 rounded-md shadow-xs focus:outline-hidden focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm font-mono dark:text-white">
  </div>

  <!-- 直连模式 -->
  <div class="p-4 bg-gray-50 dark:bg-gray-800/50 rounded-xl border border-gray-200 dark:border-gray-700">
    <div class="flex items-center justify-between">
      <div class="flex-1">
        <div class="flex items-center gap-2">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-amber-500" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M13 10V3L4 14h7v7l9-11h-7z" />
          </svg>
          <label class="text-sm font-medium text-gray-700 dark:text-gray-300">直连模式</label>
        </div>
        <p class="text-xs text-gray-500 dark:text-gray-400 mt-1">
          跳过 MiSub 预处理，直接将订阅 URL 传递给订阅转换后端
        </p>
      </div>
      <label class="relative inline-flex items-center cursor-pointer shrink-0">
        <input type="checkbox" v-model="editingSubscription.directConnect" class="sr-only peer">
        <div class="w-9 h-5 bg-gray-200 peer-focus:outline-hidden rounded-full peer dark:bg-gray-600 peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:rounded-full after:h-4 after:w-4 after:transition-all peer-checked:bg-amber-500"></div>
      </label>
    </div>
    
    <!-- 直连模式说明 -->
    <div v-if="editingSubscription.directConnect" class="mt-3 p-3 bg-amber-50 dark:bg-amber-900/20 rounded-lg border border-amber-200 dark:border-amber-800">
      <div class="flex gap-2">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-amber-500 shrink-0 mt-0.5" viewBox="0 0 20 20" fill="currentColor">
          <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z" clip-rule="evenodd" />
        </svg>
        <div class="text-sm text-amber-700 dark:text-amber-300">
          <p class="font-medium">直连模式说明：</p>
          <ul class="mt-1 text-xs space-y-0.5 text-amber-600 dark:text-amber-400">
            <li>✅ 排除/保留规则 - 将转换为 subconverter 格式</li>
            <li>❌ 协议过滤规则（proto:）- 不支持</li>
            <li>❌ 订阅前缀添加</li>
            <li>❌ 智能重命名</li>
            <li>❌ 流量统计显示</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
