---
title: "Installing a Kernel without internet connession"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by Diesel_84 on 2010-11-26
Hello,  I have Ubuntu 10.04 on my PC but I do not have access to internet (I have an Acer 3610 and before to install NDSI wrapper I have to install a Kernel). I have the most recent Kernel available on my external hardrive.
I do not know how to use sudo command to install it.
Can someone help me please?

---

### Post by dino99 on 2010-11-26
goto where the kernel you want to install is:

cd thegoodpathforyourkernel

then: sudo dpkg -i yourkernel.deb

note: replace "yourkernel" by its real name of course

---

