---
title: "broken dependencies"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by rb-falcon on 2010-11-19
Hi folks,

this is my fist post and my english is not the best, so please be patient with me.

I have a little Problem with aptitude. 

I installed a lotus notes client on my 10.04 machine. 

one of the dependencies for the ibm-lotus-notes-8.5.1.i586.deb file is 
libgnome-desktop-2 | libgnome-desktop-2-7 | libgnome-desktop-2-11 

My system has libgnome-desktop-2-17 installed. So the dependency check failes when i try to intsall the package with dpk -i.

So i installed the package with the --force-depends option

The notes client works fine. But my aptitude stops working.

Everytime i want to install or update my system it tells me, i have to resolve the missing dependencies. 

apt-get install -f wants to deinstall the notes packages.

is it possible to tell apt-get that it should not care about the notes package ? 

I hope somebody could help me. 

Tanks a lot.

---

### Post by dino99 on 2010-11-19
Welcome, and here is your gift : :)

[https://help.ubuntu.com/community/LotusNotes](https://help.ubuntu.com/community/LotusNotes)

as an alternative you can try Evolution (install from synaptic)

---

