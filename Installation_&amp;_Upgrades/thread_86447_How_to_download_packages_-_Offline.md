---
title: "How to download packages - Offline ?"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by sl9si on 2005-11-05
hi, first time in Ubuntu so please bear with me.

I am new to linux and used SUSE for the past few months. Wanted to try out Ubuntu and was wondering how to update the packages or add new packages.

For SUSE, you look for rpm packages and installed them with YAST, both online or download them somewhere else and copy into the computer for installation offline.

Understand that Ubuntu (as in Debian) there is an apt-get or Synaptic. Problem is, I do not have broadband and is living with a 56K dialup. Meaning online updates is not very effective since the line can drop midway through a long update.

Is there a way that packages can be downloaded separately somewhere else, e.g. from school's broadband connection and updated offline (just like rpm packages for SUSE) ?

Thanks in advance for the help :D

---

### Post by shandar on 2005-11-05
You can always install downloaded .deb's using 
```

sudo dpkg -i file.deb

```
but remember to look up and download all the dependencies as well!

The problem with apt-get and synaptic is that they download the packages from the servers, then invoke dpkg to install them. If you can get the deb's from another computer all you have to do is install them with dpkg as shown above.

---

### Post by samdude9 on 2005-11-05
i have exactly the same story as you!!!
total newbie used suse afew months then switch to ubuntu!
I also have the same problem!
exept different
i try to install the network card thing off add programs but cant.. no net connection.
how do i sort it???

---

### Post by nitrofurano on 2005-11-07
i'm also offline (for me 56k means being offline), which i neither took the effort of connecting Ubuntu online

And as well, i'm constantly reinstalling Ubuntu (as newbie, i'm normally always boot Ubuntu as root (it as well should be able to us configure to boot automatically into Root, which we are not allowed, i don't know why)) - running Linux always as root can sound stupid, but SU doesn't allow me full access as Root does (i'm newbie, and very console 'allergic'), and as well, other unixes like MacOS-X is defaultly booting as Root...

Constantly reinstalling Ubuntu also would mean we must always reinstall online again with Synaptic (not rare situation, i think), what i confess is a huge pain doing it on 56k connections (even worse when you're really offline....) - and when you have all .deb files downloaded (and stored in a CD or fat32 partition), you don't need to re-download constantly all stuff again...

(btw, if someone know what is needed for get running sdlBasic and FontForge - offline - please let me know - as url package locations )

(as well, another question: how Synaptic feature can be useful to us being offline? (the sollution i think is not impossible at all, what do you all think?) )

---

### Post by nitrofurano on 2005-11-07
is in brazilian-portuguese:

[http://www.linuxdicas.com.br/modules.php?name=News&file=article&sid=610&mode=&order=0&thold=0](http://www.linuxdicas.com.br/modules.php?name=News&file=article&sid=610&mode=&order=0&thold=0)

translated to english with babelfish:

[http://babelfish.altavista.com/babelfish/trurl_pagecontent?lp=pt_en&url=http%3A%2F%2Fwww.linuxdicas.com.br%2Fmodules.php%3Fname%3DNews%26file%3Darticle%26sid%3D610%26mode%3D%26order%3D0%26thold%3D0](http://babelfish.altavista.com/babelfish/trurl_pagecontent?lp=pt_en&url=http%3A%2F%2Fwww.linuxdicas.com.br%2Fmodules.php%3Fname%3DNews%26file%3Darticle%26sid%3D610%26mode%3D%26order%3D0%26thold%3D0)

please feedback here if this info is useful enough....
____________________________

Usando o APT-GET offline
Postado em Quarta, abril 16 @ 17:15:04 CDT por hyperblade 
 

 Turma foi publicado no LinuxBSD do meus amidos TDKOM uma dica do Tiago de como trabalhar com o APT-GET offline para os pinguins modem 56k que não tem como ficar baixando megas e mais megas da internet. O Tiago informa tambem que fez um How-to de como baixar os arquivos necessarios para a instalação do kde 3.1 ou gnome 2.2 ou qualquer coisa com o apt-get off line. So para terminar ele diz tambem " Acho que vai ajudar vcs. Ainda não terminei mas ja da para ter noção. " Confira Abaixo:

******************************************** 
*ATUALIZANDO A DEBIAN LOCALMENTE - BETA 0.3* 
******************************************** 

Nota de Copyright 
------------------- 

Copyright (C) 2003 Thiago Marangoni Zerbinato 

Esse manual está licenciado nos termos da GNU FDL (Free Documentation 
License). 



Introdução 
------------------- 

Quando comecei a utilizar a Debian me deparei com um enorme problema, o apt-get. Ele é 
maravilhoso, realmente é um dos pontos fortes desta distribuição, mas não para quem tem uma 
conexão discada 56k, ja que a maioria dos pacotes estão em repositórios na internet e infelizmente ainda 
hoje no Brasil a maioria das pessoas não tem acesso a Banda Larga, como eu ;), e assim fica dificil baixar 
megas e megas dos repositórios da Debian na net, mas sempre tem um jeitinho de contornar esse 
tipo de problema. 


Começando 
------------------- 

Vamos supor que você tenha a debian versão 3.0r0 e queira atualiza-la para 3.0r1, a ultima 
versão estável (11/04/2003), para isso faríamos: 

#vi /etc/apt/source.list 

Certifique-se que o repositório da debian stable encontra-se no source.list 

deb [ftp://ftp.linorg.usp.br/debian](ftp://ftp.linorg.usp.br/debian) woody main contrib non-free 
deb [ftp://ftp.linorg.usp.br/debian-non-US](ftp://ftp.linorg.usp.br/debian-non-US) woody/non-US main contrib non-free 

Para atualizarmos rodaríamos um: 
#apt-get -u upgrade 

Ai que o problema começa, já pensou ter que baixar 100mb em um modem 56k ! Inviável né! 
O que podemos fazer é obter a lista de pacotes necessários juntamente com o link do arquivo, ir 
na casa de nosso vizinho que tem banda larga ou no trampo ;) e puxar tudo, para isso faça: 

Antes de tudo 
#apt-get update 
#apt-get -qq --print-uris upgrade 

O retorno seria algo assim: 
'http://ftp.debian.org/debian/pool/main/c/cdparanoia/libcdparanoia0_3a9.8-7_i386.deb' 
libcdparanoia0_3a9.8-7_i386.deb 61130 48f61d5b3727c49682e84cac197dea68 
'http://ftp.debian.org/debian/pool/main/g/gnome-vfs2/libgnomevfs2-common_2.2.3-2_i386.deb' 
libgnomevfs2-common_2.2.3-2_i386.deb 415178 5237d3d071112ae83d7bf7ed820cce22 
'http://ftp.debian.org/debian/pool/main/f/fam/libfam0c102_2.6.9-4_i386.deb' 
libfam0c102_2.6.9-4_i386.deb 19646 5e417dfbbec74b8a5039539dbade7130 

Vamos direcionar a saída para um arquivo 
#apt-get -qq --print-uris upgrade >> fonte.txt 

Agora precisamos obter somente as URLs. 


No Windows 2000/XP do seu amigo faça (Testei no NT 4.0 da empresa e funcionou, não testei no 2000/XP mas deve funcionar) 
------------------- 

c:>for /f "delims='" %i in (fonte.txt) do @echo %i 

O parâmetro delims=' significa que o for vai pegar somente o que esta entre ' (aspas simples fica 
junto com " no teclado) 
O parâmetro @echo %i escreve as urls na tela assim: 

[http://ftp.debian.org/debian/pool/main/c/cdparanoia/libcdparanoia0_3a9.8-7_i386.deb](http://ftp.debian.org/debian/pool/main/c/cdparanoia/libcdparanoia0_3a9.8-7_i386.deb) 
[http://ftp.debian.org/debian/pool/main/g/gnome-vfs2/libgnomevfs2-common_2.2.3-2_i386.deb](http://ftp.debian.org/debian/pool/main/g/gnome-vfs2/libgnomevfs2-common_2.2.3-2_i386.deb) 
[http://ftp.debian.org/debian/pool/main/f/fam/libfam0c102_2.6.9-4_i386.deb](http://ftp.debian.org/debian/pool/main/f/fam/libfam0c102_2.6.9-4_i386.deb) 

Agora é só direcionar para um arquivo. 

c:>for /f "delims='" %i in (fonte.txt) do @echo %i >> baixar.txt 

Agora para baixar os arquivos pegue o wget for windows em ([http://mod-extreme.kit.net/wget.exe](http://mod-extreme.kit.net/wget.exe)) 

c:>wget -i baixar.txt 

Outra forma seria: 

c:>for /f "delims='" %i in (fonte.txt) do @echo %i wget -c %i 


No Linux 
------------------- 

VOU FAZER EM CASA, ESTOU NO TRAMPO, SÓ TEM NT AQUI :( 


Continuando... 
------------------- 

Agora que você tem todos os arquivos .deb é só coloca-los na pasta da sua DEBIAN em: 

#cd /var/cache/apt/archives/ 

Ou criar um repositório local, vide o manual do amigo kov em: 
[http://www.debian-br.org/view.php?doc=apt-howto-pt_BR](http://www.debian-br.org/view.php?doc=apt-howto-pt_BR) 

#apt-get -u upgrade 

Com isso o apt "acha" que já baixou os pacotes e começa a atualização ;) 


Dúvidas escreva ! 

************************************************* 
* AUTOR : THIAGO MARANGONI ZERBINATO [thiagomz] * 
* ICQ : 75311127 * 
* EMAIL : [email]LETHALTUX@YAHOO.COM.BR[/email] * 
* SITIO : [HTTP://MOD-EXTREME.KIT.NET](HTTP://MOD-EXTREME.KIT.NET) * 
* DATA : 11/04/2003 * 
*************************************************

---

