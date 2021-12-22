<template>
  <div class="container">
    <Header :quoteCount="quotes.length" :maxQuotes="maxQuotes"> </Header>
    <NewQuote @quoteAdded="addQuote"></NewQuote>
    <QuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"> </QuoteGrid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to delete it</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import Header from "./components/Header.vue";
export default {
  data() {
    return {
      quotes: ["Just a quote to see somting!"],
      maxQuotes: 10,
    };
  },
  methods: {
    addQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert("Please delete some quotes first!");
      }
      this.quotes.push(quote);
    },
    deleteQuote(id) {
      this.quotes.splice(id, 1);
    },
  },
  components: {
    QuoteGrid,
    NewQuote,
    Header,
  },
};
</script>

<style></style>
