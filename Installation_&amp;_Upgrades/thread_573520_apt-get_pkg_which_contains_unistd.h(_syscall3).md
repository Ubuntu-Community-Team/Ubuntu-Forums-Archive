---
title: "apt-get pkg which contains unistd.h(_syscall3)"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by pluz on 2007-10-11
Hi,

I have installed UBUNTU and executed apt-get for some packets (gcc, binutils, libc6-dev). I'm now trying to compile an application and I'm having a hard time with some modules. I don know why the _syscall3 for instance, can not be found. Did I miss any package ? The application I'm working with creates a vm86 and emulates a proprietary kernel for 16 bits intel processor (protected mode).
Can someone help me finding the appropriate pkg for apt-get install it ?

---

### Post by oxenfrogga on 2007-10-13
Building from source:
sudo apt-get build-dep <paket>
sudo apt-get -b source <paket>
sudo dpkg -i <paket>*deb
should do.

Otherwise execute
apt-howto

Harald

---

