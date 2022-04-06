<template>
    <!-- <ul class="news__list">
         <li v-for="article in articles" class="news__item" :key="item">{{ article.title }}
            <h5 class="title">{{ article.title }}</h5>
            <p class="description">{{ article.description }}</p>
            <img :src="article.urlToImage" class="images" />
        </li>
    </ul> -->
    <ul class="news__list">
        <div class="row">
            <div class="col-sm-4 mb-3" v-for="article in articles"> 
                <div class="card  h-100" style="border-width: 3px; border-bottom : solid #32CD32;">
                    <img class="card-img-top img-fluid" :src= article.urlToImage  alt="article images">
                    <div class="card-body">
                        <h5 class="card-title" style="text-align: left;">{{ article.title }}</h5>
                        <p class="card-text" style="text-align: left;">{{article.description}}</p>
                    <br>
                </div>
            </div>
        </div>
        </div>
    </ul>
</template>
<script>
export default {
    data() {
      return {
          articles: []
      };
    },
    created() {
        let self = this;
        fetch('https://newsapi.org/v2/top-headlines?country=us',
{
    headers: {
        'Authorization': `Bearer ${import.meta.env.VITE_NEWSAPI_TOKEN}`
    }
})
        .then(function(response) {
            return response.json();
        })
        .then(function(data) {
            console.log(data);
            self.articles=data.articles;
        });
    }
}    
</script>