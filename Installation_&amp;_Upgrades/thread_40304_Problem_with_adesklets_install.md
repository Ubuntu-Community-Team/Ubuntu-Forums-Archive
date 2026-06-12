---
title: "Problem with adesklets install"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by frodon on 2005-06-08
I download adesklet archive here : [http://prdownloads.sourceforge.net/adesklets/adesklets-0.4.9.tar.bz2?download](http://prdownloads.sourceforge.net/adesklets/adesklets-0.4.9.tar.bz2?download)

I do ./configure, all seems to be ok and when I do "make" i have some errors :

make[2]: quittant le répertoire « /home/frodon/logiciels/adesklets-0.4.9/scripting/python »
make[1]: quittant le répertoire « /home/frodon/logiciels/adesklets-0.4.9/scripting »
Making all in utils
make[1]: entrant dans le répertoire « /home/frodon/logiciels/adesklets-0.4.9/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/frodon/logiciels/adesklets-0.4.9/utils »Making all in doc
make[1]: entrant dans le répertoire « /home/frodon/logiciels/adesklets-0.4.9/doc »
Making all in imlib2
make[2]: entrant dans le répertoire « /home/frodon/logiciels/adesklets-0.4.9/doc/imlib2 »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/frodon/logiciels/adesklets-0.4.9/doc/imlib2 »
make[2]: entrant dans le répertoire « /home/frodon/logiciels/adesklets-0.4.9/doc »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/frodon/logiciels/adesklets-0.4.9/doc »
make[1]: quittant le répertoire « /home/frodon/logiciels/adesklets-0.4.9/doc »
make[1]: entrant dans le répertoire « /home/frodon/logiciels/adesklets-0.4.9 »
make[1]: Rien à faire pour « all-am ».


I think it's a perl problem, so i have 2 questions :

1- How disable perl during ./configure, I think it's a way to solve the problem.
2- If it's really a perl problem, how to solve it ? I read somewhere that this kind of error can be due to accent in XML file. I have also this kind of errors trying to install other softwares.

thanks for help

---

### Post by jimbz on 2005-06-13
I can't see any error in your output... (but I'm a newbie of course :)

---

### Post by frodon on 2005-06-14
Yes, you 're right. But I think these kind of messages are the start of my compilation problems, I will try later to install it, after serching on the web for similar problems, may be it's a simple dependency problem.
As i say before i also have these kind of messages with other softwares that I can't install, that why I think about a perl problem.

---

