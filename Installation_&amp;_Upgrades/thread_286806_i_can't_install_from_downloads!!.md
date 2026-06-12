---
title: "i can't install from downloads!!"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by fazza on 2006-10-28
ive now decided i officially do NOT know how to install from files i download for linux. I extract the file, type "./configure" like it tells me to, then i type "make". This never works. Ever. So i tried "./make" and lots of other combinations of that. What do i do? Everyone else seems to be managing!

---

### Post by rbalfour on 2006-10-28
usally the steps are

./configure
./make
./make install

re-read those docs

---

### Post by rejser on 2006-10-28
you could also install checkinstall, instead of just installing it will create a package file and install so you can handle it through synaptic.

the only difference is to change ./make install to ./make checkinstall (and ofcourse you have to have cheinstall installed)

---

