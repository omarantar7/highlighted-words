<template>
  <h1>Omar's Home Project</h1>
  <section>
    <h2>Search</h2>
    <input type="text" v-model="searchTerm" placeholder="Type to search..." />
    <p class="count">{{ count }} posts were found</p>
    <p v-html="highlightedText"></p>
  </section>
</template>

<script>
export default {
  data() {
    return {
      searchTerm: "",
      paragraph:
        "Your task is to create a search box where users can type in keywords or phrases, and your application returns results with the text being searched for highlighted. You can use any front-end framework you want (e.g. React, Angular, Vue.js, etc.).",
      count: 0,
    };
  },
  computed: {
    highlightedText() {
      if (!this.searchTerm) {
        this.count = 0;
        return this.paragraph;
      }
      const regex = new RegExp(`(${this.searchTerm})`, "gi");

      this.count = this.paragraph.match(regex)
        ? this.paragraph.match(regex).length
        : 0;
      
      return this.paragraph.replace(regex, '<span class="highlight">$1</span>');
    },
  },
};
</script>

<style>

body{
  background-color: rgb(122, 0, 122);
}
h1{
  color: #fff;
  text-align: center;
}
section {
  width: 70%;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: center;
  background-color: #fff;
  box-shadow: 0 4px 120px rgba(255, 255, 255, 0.4);
  padding: 2rem 0;
  border-radius: 2rem;
}
input {
  width: 60%;
  padding: 0.5rem 1rem;
  border-radius: 2rem;
  font-size: 1.1rem;
  outline: none;
}
p {
  font-size: 1.3rem;
  text-align: center;
}
.highlight {
  background-color: yellow;
}
.count{
  color: rgb(218, 157, 27);
}
@media (max-width:500px) {
section{
  width: 95%;
  box-shadow: 0 4px 12px rgba(255, 255, 255, 0.4);

}  
.count{
  margin: 0;
}
input{
  width: 80%;
}
}
</style>
