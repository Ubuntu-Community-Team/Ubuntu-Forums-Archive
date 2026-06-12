---
title: "Compile Driver File"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by thahir1986 on 2010-07-27
Here any know how to compile the driver file manually ?

For example i have been insert the Realtek Ethernet card in my customized kernel and kernel can't detect the card. I know the  c file 8139too.c which going to use by the realtek Ethernet card.but i don't know to how to compile the file and make this as a kernel module...help me if u know :D

---

### Post by mikewhatever on 2010-07-27
First, to compile, you need the source code. Given you have it, look for the README file for dependencies and instructions.
Generally, the procedure is as follows:
./configure
make
sudo make install

---

### Post by thahir1986 on 2010-07-28
thank very much for ur reply. I have the source code 8139too.c, but there is no configure and make file with that.

Instead of that i compiled my entire custom kernel with 8139too module, now it's works for me. Do u mean the same thing ?

---

