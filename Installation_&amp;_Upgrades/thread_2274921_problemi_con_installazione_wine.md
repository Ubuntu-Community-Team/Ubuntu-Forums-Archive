---
title: "problemi con installazione wine"
date: 2015-04-23
forum: Installation &amp; Upgrades
---

### Post by andrew218 on 2015-04-23
Ciao a tutti,

ho provato ad installare wine e dal terminale ho dato il comando:

[COLOR=#008000][I]sudo add-apt-repository ppa:ubuntu-wine/ppa

[/I][/COLOR][COLOR=#000000]E ho ricevuto questo messaggio alla fine dell'installazione:[/COLOR][COLOR=#008000][/COLOR]

E: tex-common: il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 1
E: texlive-binaries: problemi con le dipendenze - lasciato non configurato

Cosa vuol dire? Posso considerare wine installato correttamente o no?

Grazie tante per l'aiuto.

---

### Post by slickymaster on 2015-04-23
Hi andrew218, welcome to the forums.

Please be aware that this is a English spoken only forum. From the forum [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):> 
8. Write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries, and English is the common language of these forums.
If you don't feel comfortable posting in English, please try [http://forum.ubuntu-it.org/](http://forum.ubuntu-it.org/)

---

### Post by grahammechanical on 2015-04-23
I am confused. I can use google translate to understand the error messages. But here is the source of my confusion.

1) Wine is in the Ubuntu software centre. We do not need to use a PPA to get Wine.
2) I have Wine installed but I do not think that tex-common is part of wine. Tex is a separate application.
3) There are Linux versions of Tex. We can install Tex in Ubuntu without needing to use Wine.

What program are you using wine to install? Why do you wish to install a Windows version of Text when Ubuntu has a Linux version? Ubuntu has available text-common; texlive-base and texlive.

You may have success if you use the Ubuntu Software Centre to install Tex.

Regards.

---

