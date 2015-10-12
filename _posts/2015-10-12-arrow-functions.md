---
layout: post
title:  "Arrow Functions"
date:   2015-10-12 10:42:41
categories: ES6
---

O ES6 trás uma nova forma de criar funções no JavaScript, as Arrow Functions. A sintaxe é a seguinte:

```js
() => {}
```

que é o mesmo que:

```js
function() {}
```

De início vemos que a palavra reservada `function` deixa de ser usada e é adicionado a notação `=>`, mas não é apenas isso que mudou.

Uma Arrow Function não cria escopo, ou seja, o `this` não é alterado. (Para entender mais sobre o `this` recomendo esse post [http://programadorobjetivo.co/domine-javascript-this-com-3-exemplos-simples/](http://programadorobjetivo.co/domine-javascript-this-com-3-exemplos-simples/))

Isso é muito útil quando criamos funções de callback e evitamos atribuir uma variável com o `this` e utiliza-la dentro do callback ou usar a função bind para definir o escopo que o callback irá funcionar.

Exemplo:

```js
function Heisenberg() {
  this.name = 'Walter White';
}
Heisenberg.prototype.sayMyName = function() {
  setTimeout(function(){
    console.log(this.name);
  },100);
}

var heisenberg = new Heisenberg();
heisenberg.sayMyName();
```

Quando executarmos o código acima o que será escrito será uma string vazia.

Agora vamos fazer a mesma função só alterando a função anônima para uma Arrow Function:

```js
function Heisenberg() {
  this.name = 'Walter White';
}
Heisenberg.prototype.sayMyName = function() {
  setTimeout(() => {
    console.log(this.name);
  },100);
}

var heisenberg = new Heisenberg();
heisenberg.sayMyName();
```

Agora quando executarmos iremos receber no console o nome correto, Walter White :)

Além de isolar o escopo, a Arrow Function também ajuda a manter o código mais limpo, pricipalmente quando são usados alguns conceitos de programação funcional, onde vários métodos são encadeados, como num map/reduce:

```js
let arr = [1,2,3,4,5];
let sumDouble = arr.map(n => n * 2) //multiplicando todos os valores da array por 2
  .reduce((a,n) => a + n) //somando todos os valores da array

console.log(sumDouble); //30
```

Algumas considerações sobre o exemplo acima:
 - Podemos omitir as chaves (`{}`) caso a função tenha somente uma linha como no `if`;
 - Podemos omitir os parenteses caso a função receba somente um parâmetro;
 - Podemos omitir o `return` caso a função seja executa e retorne o resultado na mesma linha;

Isso é o básico para começar a usar Arrow Functions.
Até o próximo post!
