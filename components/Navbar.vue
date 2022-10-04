<template>
  <nav class="fixed w-full top-0 pt-2 px-8 bg-black text-white z-10  ">
    <div class="flex items-center justify-between">

      <!-- Header logo -->
      <div class="flex itmes-center gap-2">
        <svg class="pt-1" width="23px" height="23px" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg" fill="currentColor"><path d="M4.708 5.578L2.061 8.224l2.647 2.646-.708.708-3-3V7.87l3-3 .708.708zm7-.708L11 5.578l2.647 2.646L11 10.87l.708.708 3-3V7.87l-3-3zM4.908 13l.894.448 5-10L9.908 3l-5 10z"/></svg>
        sadikkhan
      </div>

 


      <!-- Mobile toggle -->
      <div class="md:hidden ">
        <button @click="drawer">
          <svg 
            class="h-6 w-6 fill-current text-white"
            fill="none" stroke-linecap="round" 
            stroke-linejoin="round" stroke-width="2" 
            viewBox="0 0 24 24" stroke="currentColor">
              <path d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
        </button>
      </div>

      <!-- Navbar -->
      <div class="hidden md:block ">
        <ul class="flex space-x-8 text-sm font-sans">
         
          <li><nuxt-link to="/" class="my-4 inline-block hover:underline">Home</nuxt-link></li>
          <li><nuxt-link to="/about" class="my-4 inline-block hover:underline">about</nuxt-link></li>
          <li><a href="https://imsadikkhan.medium.com/" class="my-4 inline-block">blog</a></li>
          <li><nuxt-link to="/contact" class="my-4 inline-block hover:underline">Contact</nuxt-link></li>

         
        
         </ul>
      </div>

      <!-- Background Transition -->
      <transition
        enter-class="opacity-0"
        enter-active-class="ease-out transition-medium"
        enter-to-class="opacity-100"
        leave-class="opacity-100"
        leave-active-class="ease-out transition-medium"
        leave-to-class="opacity-0">

      </transition>

      <!-- Drawer Menu -->
      <aside class="p-2 transform text-white top-0 left-0 w-full bg-black fixed h-full overflow-auto ease-in-out transition-all duration-300 z-30" :class="isOpen ? 'translate-y-0' : '-translate-y-full'">
        
        <div class="close">
          <button class="absolute top-0 right-0 mt-4 mr-4" @click="drawer">
            <svg 
              class="w-6 h-6"
              fill="none" stroke-linecap="round" 
              stroke-linejoin="round" stroke-width="2"
              viewBox="0 0 24 24" stroke="currentColor">
              <path d="M6 18L18 6M6 6l12 12"></path>
            </svg>
          </button>
        </div>

        <div  class="flex w-full items-center p-2 ">
          <div class="flex itmes-center gap-2">
        <svg class="pt-1" width="23px" height="23px" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg" fill="currentColor"><path d="M4.708 5.578L2.061 8.224l2.647 2.646-.708.708-3-3V7.87l3-3 .708.708zm7-.708L11 5.578l2.647 2.646L11 10.87l.708.708 3-3V7.87l-3-3zM4.908 13l.894.448 5-10L9.908 3l-5 10z"/></svg>
        sadikkhan
      </div>
        </div>

        <ul @click="drawer" class=" font-sans">
          <li><nuxt-link to="/" class="my-4 inline-block ">Home</nuxt-link></li>
          <li><nuxt-link to="/about" class="my-4 inline-block">about</nuxt-link></li>
          <li><a href="https://imsadikkhan.medium.com/" class="my-4 inline-block">blog</a></li>
          <li><nuxt-link to="/contact" class="my-4 inline-block">Contact</nuxt-link></li>
          </ul>
          </aside>

    </div>
  </nav>
</template>
<style>
  /* Toggle A */
input:checked ~ .dot {
  transform: translateX(100%);
  background-color: #48bb78;
}

</style>

<script>
  

export default {
  

  data() {
    return {
      isOpen: false,
      
    };
  },
  methods: {
   
    drawer() {
      this.isOpen = !this.isOpen;
    }
  },
  watch: {
    isOpen: {
      immediate: true,
      handler(isOpen) {
        if (process.client) {
          if (isOpen) document.body.style.setProperty("overflow", "hidden");
          else document.body.style.removeProperty("overflow");
        }
      }
    }
  },
  
};
</script>
