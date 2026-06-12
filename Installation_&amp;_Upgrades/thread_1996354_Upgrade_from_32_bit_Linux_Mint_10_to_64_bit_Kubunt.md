---
title: "Upgrade from 32 bit Linux Mint 10 to 64 bit Kubuntu 12"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by RickBlue70 on 2012-06-04
My upgrade from 32 bit Linux Mint 10 to 64 bit Kubuntu 12.04 has caused me problems with a Qt4 program that I created myself (a simple checkbook reconciler).
I am getting the following error when I do a "qmake CkRcn":

qmake: error while loading shared libraries: libstdc++.so.5: wrong ELF class: ELFCLASS64

Will I have to convert a c++ program to python?  ;)
Or is there another solution?

Thank you, Rick

---

### Post by dino99 on 2012-06-04
upgrading is not allowed or possible; format again to install a fresh distro.

---

### Post by RickBlue70 on 2012-06-05
> **dino99 said:**
> upgrading is not allowed or possible; format again to install a fresh distro.
===================
This is what I did from the Live/Install Kubuntu 12.04 DVD:
1. Kept my /home partition with source code intact (no formatting).
2. Formatted root partition (aka, "/").
3. Left the swap partition as is.
===================
So....
Is this an upgrade or a new install???  :(
Peace out, Rick

---

