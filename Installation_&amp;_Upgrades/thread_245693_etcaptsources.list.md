---
title: "etc/apt/sources.list"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by hudelfa on 2006-08-28
How can I reconfigure my sources.list.For example add new sources (universe/multiverse or add .tr extension.(I am from Turkey))

And when I want to update my ubuntu on my sony-vaio laptop it gives an error reads dublicate sources (smt.like this)How can I fix this..

THANKS IN ADVANCE....

---

### Post by janbockaert on 2006-08-28
you can do it in synaptic: click on settings >packet sources (or something like that, im translating from my dutch menu); or you can use this tool: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) to create a sources list from scratch, populated with some third party repositories. It worked very well for me.

---

### Post by Sboulema on 2006-08-28
you can edit the /etc/apt/source.list with your favorite text editor:

sudo nano -w /etc/apt/sources.list

After that do:

sudo apt-get update

And the new sources will have been added :)

---

### Post by Ynm on 2006-08-28
Hi,

Thanks for the advice. I have made some changes in the sourcelist, which I opened like you describe above. But how do I save those changes? There are some commands like "^X" but I'm not familiar with them. I tried to type some of them, but an error sound followed immediately.

Y

---

### Post by Ynm on 2006-08-28
Ok, the "^" seems to stand for the CTRL key
Sorry to have bothered you

Y

---

