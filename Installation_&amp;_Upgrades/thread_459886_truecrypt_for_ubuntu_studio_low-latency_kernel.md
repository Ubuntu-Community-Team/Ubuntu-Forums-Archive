---
title: "truecrypt for ubuntu studio low-latency kernel?"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by mmoalem on 2007-05-31
hi there - was trying to figure out why truecrypt wont run on my ubuntu studio until i realised i runs fine on generic kernel but it is not compiled for the low latency kernel of studio. i'm trying to avoid the compiling process which seems to get many people boged down in trouble so looking for a compiled deb package for studio's low latency kernel
anyone can help?
cheers
michel

---

### Post by capn_hector on 2007-05-31
unfortunitly in linux if you want a piece of software that does not work with apt-get you will have to compile it.  down load the source extract it then run

> sudo ./configure
sudo make
sudo make install


i dont think trucrypt has any depedency's however you will find out when you compile.  learn to compile for that will be your friend later when you find a piece of software you want but cant find a package for it.

---

### Post by mmoalem on 2007-05-31
thanks for the suggestion but i do have a question or two. if i was to compile the application how would it sits with APT? i mean there is a truecrypt package in the repository allready (for the generic kernel) and so what will happen with updates for example? how would i update with the next version? would apt recognise the installed package when it comes to installing other packages that depend on it (like forcefield)?

---

