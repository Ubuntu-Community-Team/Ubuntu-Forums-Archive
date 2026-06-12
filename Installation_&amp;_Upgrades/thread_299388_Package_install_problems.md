---
title: "Package install problems"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by stevey2005 on 2006-11-14
I've been attempting to install several packages from the Terminal command window, but keep getting the error: E:Couldn't find package ...
After successfully building the package list and dependency tree.

I'm logged in as root and have the Ubunto CD in the drive.

---

### Post by 23meg on 2006-11-14
Please copy and paste the exact commands you enter and the errors you get.

---

### Post by stevey2005 on 2006-11-14
root@uusrp-linux:/home/administrator# apt-get install proftpd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd

---

### Post by 23meg on 2006-11-14
proftpd is in the Universe repository, which you should enable.

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by voltage on 2007-01-11
> **23meg said:**
> proftpd is in the Universe repository, which you should enable.

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html)

Hi,

 May I know anyway to add extra Package using command line ?

Thanks.
Rg,
Frank Ong

---

