---
title: "dpkg-source missing from my Ubuntu install?"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by Reedbeta on 2006-03-02
Hello,

Yesterday I installed Ubuntu 5.10 on my eMachines M6809 laptop.  In the process of trying to get some drivers to work, I realized I had to download the kernel source.  I executed
```
apt-get source linux-source-2.6.12
```
After the download was finished, I recieved the error message:
```
sh: dpkg-source: command not found
```
For some reason, dpkg-source isn't installed, and I can't install it with apt-get it.  Any suggestions?

---

### Post by jrib on 2006-03-02
Have you tried installing the 'dpkg-dev' package?

If you plan on compiling things, you may just want to install the 'build-essential' package.  build-essential will pull in dpkg-dev with it.

---

### Post by Reedbeta on 2006-03-04
Installing build-essential worked.  Thanks.  Now I can compile ndiswrapper and I should be able to get my wireless card working :)

---

