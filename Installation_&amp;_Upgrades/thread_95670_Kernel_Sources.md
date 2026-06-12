---
title: "Kernel Sources?????"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by mengqing on 2005-11-27
I am trying to install Alsa-driver 1.0.10..

at ./configure step, i encoutered the following problem

checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


I have apt-getted the kernel source and linked in /usr/src/linux 
however there is no version.h file under linux/include/linux folder...

what did i miss out??

thx

---

### Post by GilGalad on 2005-11-27
You need to install the linux-headers-2.6.12-9 (which will be installed in /usr/src) and make the link /usr/src/linux to those.

---

