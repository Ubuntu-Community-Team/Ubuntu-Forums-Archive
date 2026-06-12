---
title: "Problem in the update SO version, 16.04 to 18.04"
date: 2020-12-04
forum: Installation &amp; Upgrades
---

### Post by jrxxjr on 2020-12-04
[COLOR=#203243][FONT=Helvetica]Occurs error when i update my OS Lubuntu, my current version is the 16.04, and i can upgrade to 18.04, and occurs any erros.
I update my OS Lubuntu for line command, with the command “do-release-upgrade”
I am a brazilian and my os is in portuguese, and the output error, have parts in portuguese.[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]Occurs the error follow:
“Atingido [security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") bionic-security InRelease”
“Erro [deb.opera.com/opera]("http://deb.opera.com/opera") stable InRelease”
As assinaturas a seguir não puderam ser verificadas devido à chave pública não estar disponível: NO_PUBKEY 4B8EC3BAABDC4346
Obtidos 2.591 B em 0s (0 B/s)[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]Erro durante a atualização[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]Um problema ocorreu durante a atualização. Isso geralmente pode ser
por problemas de rede, por favor verifique a sua conexão de rede e
tente novamente.[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]Restaurando o estado original do sistema[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]Abortando
Lendo listas de pacotes… Feito
Construindo árvore de dependências
Lendo informação de estado… Feito[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]/////
The errors are of verification public key of the package opera, the key is 4B8EC3BAABDC4346.[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]And do not have problem in my network, my network do not have a proxy, and the signal of my internet is very good.[/FONT][/COLOR]

---

### Post by ajgreeny on 2020-12-04
Before you run a ***do-release-upgrade*** command your system must be fully updated for the version currently installed.

Lubuntu 16.04 lost support about 18 months ago and has not been upgraded on your system since April 2019.

You also must remove or disable any repositories that are not default for the OS in question; you should therefore remove opera browser and any repository for it.

In all honesty I think you would be best served by not trying to upgrade but by backing up all your personal files and then clean installing a fully supported version of whatever DE version you want.

---

### Post by Impavidus on 2020-12-05
Lubuntu 16.04 is dead. The parts it has in common with Ubuntu 16.04 (the main repository, mostly) have 4 months of support left, but history has shown that such partially supported OSs are more likely to break on regular upgrades. And obviously they are less secure than fully supported OSs.

Lubuntu 18.04 has 4 months of support left. I wouldn't install it. That brings you to Lubuntu 20.04. There's no upgrade from Lubuntu 18.04 to 20.04 (and I wouldn't recommend a double upgrade anyway). So my suggestion is a clean install of 20.04.

Before a release upgrade, any third party software sources and the software installed from those must be disabled. In your case that means removing opera and disabling the repository from where it came.

---

