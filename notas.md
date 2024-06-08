# Modulo 9 - jQuery
## Notas
### Aula 1 - Selecione elementos
#### **Sobre a Aula**
* entender o benefício de usar o jQuery ao desenvolver aplicações web;
* aplicar seletores apropriados no jQuery;
* usar métodos e funções do jQuery para realizar manipulações nos elementos do DOM.
#### **Anotações**
Ferramenta importante que vai aumentar as funções que temos com JS, podemos construir projetos pequenas que vão ter complementos importantes, podemos construir animações, transições, são plugins que completam o JS  
nessa aula inicialmente estilizamos a página do material de apoio: uma galeria de imagens que consiste num titulo com um botão de 'nova imagem' e um formulário com input de url e um botão de adicionar e um botão de cancelar  
agora abrimos a pagina jquery.com e fazemos o 'download' do jQuery 3.7.1, basicamente isso abre uma aba com linhas e mais linhas de script cujo url nós copiamos para uma tag script dentro do html, em paralelo abrimos outra tag script com src no arquivo main.js  
para testar se o jQuery foi importado corretamente usamos o (cifrão)(document).ready(function(){
    alert('Olá mundo!')  
})  
isso criou um alerta na nossa página, ou seja, o jQuery está funcionando devidamente.  
em seguida, para um segundo teste, substituimos o alert por:  
console.log(document.querySelector('header button'))  
console.log($('#botao-cancelar))  
assim, no console primeiro aparece o elemento e em seguida um array de somente um item cujo item é o botão de cancelar  
### Aula 2 - Manipule eventos
#### **Sobre a aula**
* identificar dierentes tipos de eventos;
* aplicar eventos a elementos;
* criar comportamentos interativos específicos para cada tipo de evento.
#### **Anotações**
o professor demonstrou maneiras simplificadas através do jQuery de substituir a função addEventListener, são essas:  
  
$('header button').click(function(){
    alert('Expandir formulário')  
})  
  
$('form').on('submit', function(e){
    console.log('submit');  
    e.preventDefault();  
})  
  
assim aprendemos a adicionar eventos utilizando jQuery
### Aula 3 - Aplique efeitos e animações
#### **Sobre a aula**
* usar funções para aplicar efeitos de expansão e recolhimento a elementos;
* praticar a seleção de elementos do jQuery;
* usar animações como slideUp e slide Down.
#### **Anotações**
inicialmente o formulário não sera exibido, assim definimos seu display para none  
em seguida vamos, dentro da função click do header button, selecionar o elemento form e expandi-lo com a função slideDown()  
configuramos então o slideUp() para o evento click no seletor ('#botao-cancelar'), podiamos tambem fazer selecionando o form chamando a função on para o evento 'reset' e dentro do callback selecionar o 'form' e chamar a função slideUp, ambas as maneiras funcionam de maneira identica  
### Aula 4 - Manipule DOM
#### **Sobre a aula**
* compreender o conceito de manipulação do DOM usando a biblioteca jQuery;
* criar elementos usando métodos e funções do jQuery;
* aplicar animações e efeitos visuais aos elementos HTML criados dinamicamente.
#### **Anotações**
adicionei 3 vezes a imagem do kanji de shiatsu numa ul, (na aula o professor utiliza 3 imagens diferentes, mas como essas não foram disponibilizadas eu utilizei uma imagem que eu tinha salva no meu computador)  
dentro dos li adicionamos também uma div com a class .overlay-imagem-link e dentro dessa div um link para a imagem dizendo: 'ver a imagem em tamanho real', esse elemento possui a propriedade target='_blank' isso faz com que ao ser clicado o link abre uma nova aba.  
estilizamos o display da ul para flex e o flex-wrap para wrap  
em seguida estilizamos os li para ter o max-width: 25%, removemos os pontinhos com list-style: none, definimos o position relative já que dentro dele a div vai ter position absolute, definimos altura máxima para 280 px e cortamos o excedente com overflow-y: hidden;  
definimos o width das img para 100%  
em seguida estilizamos a div (utilizamos ctrl+d para selecionar todas as divs ao mesmo tempo e adicionar-lhes a classe), definimos o padding, definimos o position absolute com left e bottom em 0 e definimos o opacity para 0, para que esse elemento fique oculto  
estilizamos o link em si dentro da div definindo sua cor para branca e removemos o text-decoration  
por fim definimos que ul li:hover .overlay-imagem-link opacity:1;, assim, ao passarmos o mouse sobre os list item a opacity da div vai de 0 a 1, apresentando o link com a mensagem 'ver imagem em tamanho real'  
também adicionamos a propriedade transition a div com os parametros all ease .5s, para que o surgimento do link se de com uma animação de transição  
  
agora vamos codificar o mecanismo de adição de elementos  
primeiro, dentro da função on, que já possui o e.preventDefault();, vamos criar duas **const**  
primeiro a **const** enderecoNovaImagem = (cifrao)(#endereco-imagem-nova).val();  
depois a **const** novoItem = (cifrao)('li style="display:none;"/li')  
depois utilizamos a função appendTo(novoItem) para adicionar a tag img com enderecoNovaImagem e a nova div com enderecoNovaImagem a novoItem, por fim adicionamos novoItem a ul usando a mesma função e fazemos com que novoItem apareça com a função fadeIn(2000), 2000 milisegundos, finalizamos a função zerando novamente o valor do input selecionando com o cifrão o elemento e zerando seu valor com a função val();  

