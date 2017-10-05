# Exemplo de aplicação CRUD em Vue.js 2 

### Introdução

O objetivo dessa aplicação é mostrar funções básicas de CRUD em Vue.js 2 e mostrar os componentes definidos e templates associados a estes.

#### Componentes definidos

List

> Componente responsável para carregar a lista de produtos
```vuejs
var List = Vue.extend({
  template: '#product-list',
  data: function () {
    return {products: products};
  }
});
```

Product

> Responsável por renderizar os detalhes de um produto
```vuejs
var Product = Vue.extend({
  template: '#product',
  data: function () {
    return {product: findProduct(this.$route.params.product_id)};
  }
});
```

ProductEdit

> Responsável pela atualização de um produto já existente
```vuejs
var ProductEdit = Vue.extend({
  template: '#product-edit',
  data: function () {
    return {product: findProduct(this.$route.params.product_id)};
  },
  methods: {
    updateProduct: function () {
      var product = this.product;
      products[findProductKey(product.id)] = {
        id: product.id,
        name: product.name,
        author: product.author,
        description: product.description,
        price: product.price,
        code: product.code
      };
      router.push('/');
    }
  }
});
```

ProductDelete

> Responsável pela remoção de um produto
```vuejs
var ProductDelete = Vue.extend({
  template: '#product-delete',
  data: function () {
    return {product: findProduct(this.$route.params.product_id)};
  },
  methods: {
    deleteProduct: function () {
      products.splice(findProductKey(this.$route.params.product_id), 1);
      router.push('/');
    }
  }
});
```

AddProduct

> Responsável por cadastrar um produto novo
```vuejs
var AddProduct = Vue.extend({
  template: '#add-product',
  data: function () {
    return {product: {name: '', author: '', description: '', price: '', code: ''}}
  },
  methods: {
    createProduct: function() {
      var product = this.product;
      products.push({
        id: Math.random().toString().split('.')[1],
        name: product.name,
        author: product.author,
        code: product.code,
        description: product.description,
        price: product.price
      });
      router.push('/');
    }
  }
});
```

#### URL definidos

Lista de produtos => /

Detalhes de um produto => /product/:product_id

Cadastro de um produto => /add-product

Atualização da informação de um produto => /product/:product_id/edit

Remoção de um produto => /product/:product_id/delete

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

### Conclusão

Como já havia vários exemplos de CRUD implementados na Internet, este exercício foi baseado em https://codepen.io/mevdschee/pen/BpbEbj. A partir desse projeto, material de API da vuejs e alguns tutoriais citados na seçao da referência foram estudados para entender o funcionamento do código e em seguida fazer uma pequena adaptaçao. 

A experiência mostrou um grau de simplicidade de começar o desenvolvimento com vuejs. Foi visto que existem muitas outras funcionalidades interessantes a medida que a documentação foi estudada. 



### Referências

https://codepen.io/mevdschee/pen/BpbEbj

https://vuejs.org/v2/api

https://scotch.io/tutorials/getting-started-with-vue-router

https://medium.com/codingthesmartway-com-blog/vue-js-2-quickstart-tutorial-2017-246195cfbdd2
