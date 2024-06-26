<div align="center">
<h1>Aprenda conceitos de git</h1>
<h4>Um tutorial interativo de git, destinado a ensinar como o git funciona, não apenas quais comandos executar.</h3>
<i>Esse treinamento é quase de graça, basta deixar uma star ⭐ no <a href="https://github.com/venancio2000/treinamento-git-master">repositório</a>.😊</i>
</div>
<br>

Então você quer usar o git, certo?

Mas você não quer apenas aprender comandos, quer entender o que está usando?

Então isso é para você!

Vamos começar!

> Esse treinamento é uma tradução e adaptação do excelente conteúdo [Learn git concepts, not commands](https://dev.to/unseenwizzard/learn-git-concepts-not-commands-4gjc), de [Nicola Riedmann](https://www.linkedin.com/in/nicola-michel-henry-riedmann/). Thanks Nico 😊

---

> Com base no conceito geral da postagem do blog de Rachel M. Carmena em [How to teach Git](https://rachelcarmena.github.io/2018/12/12/how-to-teach-git.html).
>
> Embora eu ache muitos tutoriais de git na internet focados no que fazer, ao invés de como as coisas funcionam, o recurso mais inestimável para ambos (e a fonte para este tutorial!) é o [Pro Git Book (traduzido para PT-BR)](http://git-scm.com/book/pt-br) e a [página de referência](https://git-scm.com/docs).
>
> Então, se você ainda estiver interessado quando terminar aqui, vá conferir! Espero que o conceito um pouco diferente deste tutorial o ajude a entender todos os outros recursos git detalhados lá.

---
- [Visão geral](#visão-geral)
- [Obtendo um _Remote Repository_](#obtendo-um-remote-repository)
- [Adicionando coisas novas](#adicionando-coisas-novas)
- [Fazendo mudanças](#fazendo-mudanças)
- [Ramificação (Branch)](#ramificação-branch)
- [Mesclagem (Merging)](#mesclagem-merging)

---

## Visão geral

Na imagem abaixo existem 4 caixas. Uma delas fica sozinha, enquanto as outras três estão agrupadas no que chamarei de _Development Environment_.

<!-- components.png -->
![componentes do git](https://user-images.githubusercontent.com/29241659/87479229-79442f00-c601-11ea-8ca6-f9a8070a17e5.png)

Vamos começar com o que está sozinho. O _Remote Repository_ é para onde você envia as alterações quando deseja compartilhá-las com outras pessoas e de onde obtém as alterações. Se você já usou outros sistemas de controle de versão, não há nada de interessante nisso.

O _Development Environment_ é o que você possui na sua máquina local.
As três partes são seu _Working Directory_, a _Staging Area_ e o _Local Repository_. Aprenderemos mais sobre eles quando começarmos a usar o git

Escolha um local em que você deseja colocar seu _Development Environment_.
Basta ir para a sua pasta pessoal ou para onde você quiser colocar seus projetos. Você não precisa criar uma nova pasta para o seu _Dev Environment_.

## Obtendo um _Remote Repository_

Agora queremos pegar um _Remote Repository_ e colocar o que está nele na sua máquina.

Eu sugiro que usemos o repositório [github.com/PauloGoncalvesBH/treinamento-git](https://github.com/PauloGoncalvesBH/treinamento-git) no nosso treinamento.

> Para fazer isso use o comando `git clone https://github.com/PauloGoncalvesBH/treinamento-git.git`
> 
> Mas, ao seguir este tutorial, você precisará enviar as alterações feitas no seu _Dev Environment_ de volta ao _Remote Repository_, e o github não permite que uma pessoa faça isso no repositório de outra pessoa, por isso o melhor a fazer é criar um [_fork_](https://guides.github.com/activities/forking). Há um botão para fazer isso no canto superior direito desta página.

Agora que você já possui uma cópia do meu _Remote Repository_ na sua conta do github por ter feito o _fork_, é hora de colocar isso em sua máquina.

Para isso usamos `git clone https://github.com/{SEU USUÁRIO}/treinamento-git.git`

Como você pode ver no diagrama abaixo, isso copia o _Remote Repository_ em dois lugares, seu _Working Directory_ e o _Local Repository_.
Agora você vê como o git é um controle de versão _distribuído_. O _Local Repository_ é uma cópia do _Remote_ e age exatamente como ele. A única diferença é que você não o compartilha com ninguém.

O que o `git clone` também faz é criar uma nova pasta no local aonde você executou o comando. Deve haver uma pasta `treinamento-git` agora. Abra-a.

<!-- clone.png -->
![Clonando o repositório remoto](https://user-images.githubusercontent.com/29241659/87479277-92e57680-c601-11ea-9f8f-a9082fb24e90.png)

## Adicionando coisas novas

Alguém já colocou um arquivo chamado `Alice.txt` no _Remote Repository_. É meio solitário lá, então vamos criar um novo arquivo e chamá-lo de `Bob.txt`.

O que você acabou de fazer é adicionar um arquivo no seu _Working Directory_.
Existem dois tipos de arquivos no seu _Working Directory_: Arquivos _tracked_, que o git conhece, e _untracked_, arquivos que o git (ainda) não conhece.

<!-- tracking_files.png -->
![Rastreando arquivos](https://user-images.githubusercontent.com/29241659/87481065-f91fc880-c604-11ea-8c30-97a963fb0533.png)

Para ver o que está acontecendo no seu _Working Directory_ execute `git status`, que informará em que branch você está, se o seu _Local Repository_ é diferente do _Remote_ e os arquivos _tracked_ e _untracked_.

Você verá que `Bob.txt` não é rastreado (_untracked_) e o `git status` até lhe diz como mudar isso.
Na figura abaixo, você pode ver o que acontece quando você segue a dica e executa `git add Bob.txt`: Você adicionou o arquivo à _Staging Area_, onde você coleta todas as alterações que deseja incluir no _Repository_.

<!-- add.png -->
![Incluindo mudanças na staging area](https://user-images.githubusercontent.com/29241659/87479352-b9a3ad00-c601-11ea-975f-2c5eb0cefffe.png)

Quando você adicionar todas as suas alterações (que agora é apenas adicionar `Bob.txt`), você estará pronto para fazer o _commit_ do que acabou de fazer no _Local Repository_.

As alterações que você fez são uma parte significativa do trabalho, portanto, quando você executa o `git commit`, um editor de texto será aberto e permitirá que você escreva uma mensagem dizendo tudo o que você acabou de fazer. Quando você salva e fecha o arquivo de mensagens, seu _commit_ é adicionado ao _Local Repository_.

<!-- commit.png -->
![Commitando no repositório local](https://user-images.githubusercontent.com/29241659/87479385-c922f600-c601-11ea-8287-22eb200a6a32.png)

Você também pode adicionar sua _mensagem de commit_ na linha de comando se você chamar `git commit` assim: `git commit -m "Adicionar Bob"`. Mas como você deseja escrever [boas mensagens de commit](https://chris.beams.io/posts/git-commit/), você deve gastar um tempo estudando e usar o editor.

Agora suas alterações estão no seu repositório local, o que é um bom local para elas, desde que ninguém mais precise delas ou você ainda não esteja pronto para compartilhá-las.

Para compartilhar seus commits com o _Remote Repository_ você precisa empurrá-los (`push`).

<!-- push.png -->
![Enviando para o repositório remoto](https://user-images.githubusercontent.com/29241659/87479430-da6c0280-c601-11ea-837a-105a696abb52.png)

Depois de executar o comando `git push` as alterações serão enviadas para o _Remote Repository_. No diagrama abaixo, você vê o estado após o seu `push`.

<!-- after_push.png -->
![Estado de todos os componentes após enviar as alterações](https://user-images.githubusercontent.com/29241659/87479605-2c148d00-c602-11ea-8103-0e72183059ab.png)

## Fazendo mudanças
Até agora apenas adicionamos um novo arquivo. Obviamente a parte mais interessante do controle de versão é a alteração de arquivos.

Dê uma olhada no arquivo `Alice.txt`.

Na verdade ele contém algum texto, mas `Bob.txt` não, então vamos mudar isso e colocar `Oi!! Eu sou o Bob. Eu sou novo aqui.`.

Se você executar o `git status` agora, verá que o `Bob.txt` está modificado (`modified`).
Nesse estado as alterações estão apenas no seu _Working Directory_.

Se você deseja ver o que mudou no seu _Working Directory_, você pode executar o `git diff` e ver a seguinte saída:

```Diff
diff --git a/Bob.txt b/Bob.txt
index e69de29..3ed0e1b 100644
--- a/Bob.txt
+++ b/Bob.txt
@@ -0,0 +1 @@
+Oi!! Eu sou o Bob. Eu sou novo aqui.
```

Vá em frente e execute `git add Bob.txt` como você fez anteriormente. Como sabemos, isso move suas alterações para a _Staging Area_.

Eu quero ver as mudanças que acabamos de realizar, então vamos executar `git diff` novamente! Você notará que desta vez a saída está em branco. Isso acontece porque o `git diff` opera apenas nas alterações no seu _Working Directory_.

Para mostrar quais mudanças já estão na _Staging Area_, podemos executar `git diff --staged` e veremos a mesma saída diff de antes.

Acabei de notar que colocamos dois pontos de exclamação após o 'Oi'. Eu não gosto disso, então vamos mudar o `Bob.txt` novamente, para que seja apenas 'Oi!'

Se agora rodarmos `git status`, veremos que existem duas mudanças: A que já enviamos para a _Staging Area_, onde adicionamos texto, e a que acabamos de fazer, que ainda está apenas no diretório de trabalho.

Podemos dar uma olhada no `git diff` entre o _Working Directory_ e o que já enviamos para a _Staging Area_, para mostrar o que mudou desde que nos sentimos prontos para realizar um commit das mudanças.

```Diff
diff --git a/Bob.txt b/Bob.txt
index 8eb57c4..3ed0e1b 100644
--- a/Bob.txt
+++ b/Bob.txt
@@ -1 +1 @@
-Oi!! Eu sou o Bob. Eu sou novo aqui.
+Oi! Eu sou o Bob. Eu sou novo aqui.
```

Como a mudança é o que queríamos, vamos executar `git add Bob.txt` para enviar o estado atual do arquivo para _stage_.

Agora estamos prontos para realizar o `commit` com o que acabamos de fazer. Eu criei o commit com `git commit -m "Alterar texto de Bob"` porque senti que, para uma mudança tão pequena, escrever uma linha seria suficiente.

Como sabemos, as alterações estão agora no _Local Repository_.
Ainda podemos querer saber que mudança acabamos de commitar e o que havia antes.

Podemos fazer isso comparando commits.
Todo commit no git tem um hash exclusivo pelo qual é referenciado.

Se dermos uma olhada no `git log`, não apenas veremos uma lista de todos os commits com _hash_, como _Autor_ e _Data_, também veremos o estado do nosso _Local Repository_ e as informações locais mais recentes sobre _branches remotas_ .

No momento, o `git log` se parece com isso:

```ShellSession
commit 87a4ad48d55e5280aa608cd79e8bce5e13f318dc (HEAD -> master)
Author: {VOCÊ} <{SEU EMAIL}>
Date:   Sun Jan 27 14:02:48 2019 -0300

    Alterar texto de Bob

commit 8af2ff2a8f7c51e2e52402ecb7332aec39ed540e (origin/master, origin/HEAD)
Author: {VOCÊ} <{SEU EMAIL}>
Date:   Sun Jan 27 13:35:41 2019 -0300

    Adicionar Bob

commit 71a6a9b299b21e68f9b0c61247379432a0b6007c \1
Author: Paulo Gonçalves <commit@github.com>
Date:   Fri Jan 25 20:06:57 2019 -0300

    Adicionar Alice

commit ddb869a0c154f6798f0caae567074aecdfa58c46
Author: Paulo Gonçalves <commit@github.com>
Date:   Fri Jan 25 19:25:23 2019 -0300

    Adicionar texto do tutorial

    Todas as alterações no tutorial são compactadas neste commit para manter o log livre de desorganização que o distrai.
```

Aqui vemos algumas coisas interessantes:
* Os dois primeiros commits são feitos por mim.
* Seu commit inicial para adicionar Bob é o _HEAD_ atual da branch _master_ no _Remote Repository_. Veremos isso novamente quando falarmos sobre ramificações (branches) e obter alterações remotas.
* O último commit no _Local Repository_ é o que acabamos de fazer e agora sabemos o seu hash.

> Observe que os hashes dos commits serão diferentes para você. Se você quiser saber exatamente como o git chega a esses IDs de revisão, dê uma olhada [neste artigo sobre a anatomia de um commit](https://blog.thoughtram.io/git/2014/11/18/the-anatomy-of-a-git-commit.html).

Para comparar esse commit e o anterior, podemos utilizar `git diff <commit>^!` (Onde `^!` diz ao git para comparar o commit com o que veio antes dele). Portanto, neste caso, eu executo `git diff 87a4ad48d55e5280aa608cd79e8bce5e13f318dc^!`.

Também podemos fazer o `git diff 8af2ff2a8f7c51e2e52402ecb7332aec39ed540e 87a4ad48d55e5280aa608cd79e8bce5e13f318dc` para o mesmo resultado e, em geral, comparar quaisquer dois commits. Note que o formato aqui é `git diff <de commit> <para commit>`, então nosso novo commit fica em segundo.

No diagrama abaixo você vê novamente os diferentes estágios de uma alteração e os comandos diff correspondentes.

<!-- diffs.png -->
![Estados de uma mudança e comandos diff relacionados](https://user-images.githubusercontent.com/29241659/87479633-36cf2200-c602-11ea-84f4-46cf255e8f7b.png)

Agora que temos certeza de que fizemos a alteração que queríamos, vá em frente e execute `git push`.

## Ramificação (Branch)

Outra coisa que torna o git excelente é o fato de que trabalhar com ramificações é realmente uma parte fácil e essencial de como você trabalha com o git.

De fato, trabalhamos em uma branch desde que começamos.

Quando você clona o _Remote Repository_, seu _Dev Environment_ inicia automaticamente na ramificação principal do repositório, ou seja, _master_.

> Há um movimento atual para a branch principal deixar de ser chamada como _master_ e passar a ser _trunk_ ou _main_. Linux, Github e outras companhias estão adotando a nova nomenclatura. É uma ótima proposta e totalmente alinhada ao movimento `#BlackLivesMatter`. Você pode entender mais lendo o artigo [The bigger picture behind the GitHub master branch name change](https://dev.to/sylviapap/the-bigger-picture-behind-the-github-master-branch-name-change-35h8).

A maioria dos fluxos de trabalho com o git incluem fazer suas alterações em uma _branch_ antes de você mesclá-las (`merge`) novamente na _master_.
Normalmente você estará trabalhando por conta própria até que esteja pronto e confiante das suas alterações, que poderão ser mescladas (mergeadas) na _master_.

> Muitos gerenciadores de repositório git, como o _GitLab_ e o _GitHub_, permitem que as branches sejam _protegidas_, o que significa que nem todo mundo pode simplesmente empurrar (`push`) as mudanças pra lá. O _master_ geralmente é protegido por padrão.

Não se preocupe, retornaremos a todas essas coisas com mais detalhes quando precisarmos delas.

No momento queremos criar uma branch para fazermos algumas alterações. Talvez você queira apenas tentar algo por conta própria e não mexer com o estado de trabalho na sua branch _master_, ou não pode empurrar (`push`) para a _master_.

As branches ficam no _Local_ e no _Remote Repository_. Quando você cria uma nova branch, o conteúdo dessa branch será uma cópia de qualquer ramificação em que você esteja trabalhando no momento.

Vamos fazer algumas alterações no `Alice.txt`! Que tal colocarmos algum texto na segunda linha?

Queremos compartilhar essa mudança, mas não colocá-la na _master_ imediatamente, então vamos criar uma ramificação para ela usando `git branch <branch name>`.

Para criar uma nova branch chamada `change_alice`, você pode executar o comando `git branch change_alice`.

Isso adiciona a nova branch ao _Local Repository_.

Enquanto seu _Working Directory_ e _Staging Area_ realmente não se importam com branches, você sempre cria `commit` com a branch em que está atualmente.

Você pode pensar em _branches_ no git como ponteiros, apontando para uma série de confirmações. Quando você faz um `commit`, você adiciona o que você está apontando no momento.

Apenas adicionar uma branch não o leva diretamente para lá, apenas cria um ponteiro.
De fato, o estado em que seu _Local Repository_ está atualmente, pode ser visto como outro ponteiro, chamado _HEAD_, que aponta para qual branch e commit você está atualmente.

Se isso parecer complicado, os diagramas abaixo ajudarão a esclarecer um pouco as coisas:

<!-- add_branch.png -->
![Estado após adicionar branch](https://user-images.githubusercontent.com/29241659/87479558-1bfcad80-c602-11ea-9ea6-a7611215540e.png)

Para mudar para a nossa nova branch, você terá que usar o comando `git checkout change_alice`. O que isso faz é simplesmente mover o _HEAD_ para a branch que você especificar.

> Como você normalmente deseja mudar para uma branch logo após criá-la, existe a conveniente opção `-b` disponível para o comando `checkout`, que permite realizar `checkout` diretamente em uma branch nova, para que você não precisa criá-la de antemão.
>
> Então, para criar e mudar para a nossa branch `change_alice`, também poderíamos ter executado `git checkout -b change_alice`. Mais simples, não?

<!-- checkout_branch.png -->
![Estado após trocar de branch](https://user-images.githubusercontent.com/29241659/87479588-24ed7f00-c602-11ea-8a4b-c733d1da4826.png)

Você notará que seu _Working Directory_ não mudou e o fato de termos modificado `Alice.txt` ainda não está relacionado à branch em que estamos inseridos. Agora você pode adicionar (`add`) e fazer `commit` da alteração em `Alice.txt`, como fizemos no _master_ antes, que irá mover o arquivo para a _Staging Area_ (nesse ponto ainda não está relacionado à branch) e, finalmente, _'committar'_ sua alteração na branch `change_alice`.

Há apenas uma coisa que você não pode fazer ainda. Tente enviar (`git push`) suas alterações para o _Remote Repository_.

Você verá o seguinte erro e - como o git está sempre pronto para ajudar - uma sugestão de como resolver o problema:

```ShellSession
fatal: The current branch change_alice has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin change_alice 
```

Mas não queremos fazer isso às cegas. Estamos aqui para entender o que realmente está acontecendo. Então, o que são _upstream branches_ e _remotes_?

Lembra quando clonamos o _Remote Repository_ há um tempo atrás? Nesse ponto, ele não continha apenas este tutorial e `Alice.txt`, mas na verdade duas ramificações.

Quando copiamos as coisas no _Remote Repository_ para o seu _Dev Environment_, algumas etapas extras ocorreram embaixo do capô.

O Git configurou o _remote_ do seu _Local Repository_ para ser o _Remote Repository_ que você clonou e deu a ele o nome padrão `origin`.

> Seu _Local Repository_ pode rastrear vários _remotes_ e eles podem ter nomes diferentes, mas seguiremos apenas com a `origin` nesse tutorial.

Em seguida, ele copiou as duas branches remotas no seu _Local Repository_ e, finalmente, alterou para a _master_ para você (`git checkout`).

Ao fazer isso, outra etapa implícita acontece. Quando você faz `checkout` de um nome de uma branch que tenha uma correspondência exata nas branches remotas, você obterá uma nova branch _local_ que está vinculada à branch _remote_. A branch _remote_ é a branch _upstream_ do seu _local_.

Nos diagramas anteriores, você pode ver apenas as branches locais que possui. Você pode ver essa lista de branches locais executando o comando `git branch`.

Se você quiser ver também as branches remotas que seu _Local Repository_ conhece, você pode executar `git branch -a` para listar todas elas.

<!-- branches.png -->
![Branches remotas e local`](https://user-images.githubusercontent.com/29241659/87479573-2159f800-c602-11ea-8b88-d77409c18278.png)

Agora podemos executar o comando sugerido `git push --set-upstream origin change_alice`, e empurrar (`push`) as alterações em nossa branch para um novo _remote_. Isso criará a branch `change_alice` no _Remote Repository_ e definirá o nosso _local_ `change_alice` para rastrear essa nova branch.

> Existe outra opção se realmente queremos que nosso ramo rastreie algo que já existe no _Remote Repository_. Talvez um colega já tenha promovido algumas mudanças, enquanto estávamos trabalhando em alguma questão relacionada em nossa branch local, e gostaríamos de integrar as duas. Então poderíamos simplesmente definir o _upstream_ para a nossa branch `change_alice` como um novo _remote_ usando `git branch --set-upstream-to=origin/change_alice` e daí para rastrear a branch _remote_.

Depois disso, dê uma olhada no seu _Remote Repository_ no github, sua branch estará lá, pronto para outras pessoas verem e trabalharem.

Vamos ver como você pode obter as alterações de outras pessoas em seu _Dev Environment_ em breve, mas primeiro trabalharemos um pouco mais com as branches, para introduzir todos os conceitos que também entram em jogo quando obtemos novidades do _Remote Repository_.

## Mesclagem (Merging)

Como você e todo mundo em geral trabalharão em branches, precisamos conversar sobre como obter alterações de uma branch para outra, _mergeando_ elas.

<!-- NO CONFLICT -->
Acabamos de alterar o arquivo `Alice.txt` na branch `change_alice`, e eu diria que estamos felizes com as alterações que fizemos.

Se você executar `git checkout master`, o `commit` que fizemos na outra branch não estará lá. Para colocar as alterações na master, precisamos mesclar (`merge`) a branch `change_alice` na master.

Note que você sempre mescla uma branch específica com a que você está atualmente.