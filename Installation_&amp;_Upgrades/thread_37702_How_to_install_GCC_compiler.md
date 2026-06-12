---
title: "How to install GCC compiler"
date: 2005-05-28
forum: Installation &amp; Upgrades
---

### Post by ymtoh on 2005-05-28
hey ... do anyone know how to install GCC compiler? and anyone got any site to download the binary version? 

i think i will rather know how to install GCC from source. thank you

---

### Post by SGC on 2005-05-28
GCC homepage: [http://gcc.gnu.org/](http://gcc.gnu.org/)
you can find there both the binary and source packages

The easiest way to install GCC, from the terminal:
sudo apt-get install gcc

---

### Post by ymtoh on 2005-05-28
i have been there when i tried looking for instructions to install gcc 

i tried reading the instructions... but then i couldn't understand... can u explain it futher for me????

---

### Post by SGC on 2005-05-28
I don't know how to compile gcc from the source, and I don't think this is necessary; all you have to do is to open the terminal and type:
apt-get install gcc

apt-get will downloads gcc with all it's dependencies and will install it to you.

---

### Post by ymtoh on 2005-05-31
[QUOTE=SGC]I don't know how to compile gcc from the source, and I don't think this is necessary; all you have to do is to open the terminal and type:
apt-get install gcc

apt-get will downloads gcc with all it's dependencies and will install it to you.[/QUOTE]
 not all distro hav the command of *apt-get install gcc* right? bcos i would like to learn the way so that i can use it in other distro as well..

thanx

---

### Post by SGC on 2005-05-31
I didn't know, I thought you want to install it on Ubuntu. 

Although not all disto have apt-get , there is a similar commands and package managment tools, that downaload and install the software that you want.

---

### Post by tread on 2005-05-31
Yep, you almost never will have to compile gcc from source .. which will be a long bootstrapped procedure .. definitely not worth the effort. Every distro will come with gcc ..

---

### Post by SNo0py on 2005-05-31
[QUOTE=tread]Yep, you almost never will have to compile gcc from source .. which will be a long bootstrapped procedure .. definitely not worth the effort. Every distro will come with gcc ..[/QUOTE]
... but if he wants, he can try out Gentoo - trust me, after some days compiling stuff, he does not want to compile gcc by himself anymore...

---

