---
title: "transfer settings from one computer to another"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by seng1978 on 2007-08-18
alrite, after browsing through google and ubuntu forums day after day i come to the conclusion to open a new thread. Here I am.

I got 5 computers here with different specs(motherboard, CPU,RAM,etc)

I got ubuntu running for a few weeks on my computer and I love what it does now. Now the thing is i want to intall ubuntu on the other 5 computers having the same setting as me. i do not want to go through the sudo apt-get update/upgrade wine,etc on every single computer

any suggestions? thanks

---

### Post by raja on 2007-08-18
Since they have different hardware, you cannot make images of the disk and copy it over. 
One option is to use [reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1") to customize the Ubuntu cd with the extra apps you want and then use that to install on the other computers. Dont know if that is worth the trouble though. 
The simpler way may be to put all the apt-get installs in a script and run it in each pc. You might even be able to download the deb files only once, put it on a cd and then use them from there.

---

### Post by por100pre1 on 2007-08-18
You can use Grsync to copy your files to an ext HDD and then copt them to to other PC. You can use APTonCD to get your programs installed in your other PC easily.

---

