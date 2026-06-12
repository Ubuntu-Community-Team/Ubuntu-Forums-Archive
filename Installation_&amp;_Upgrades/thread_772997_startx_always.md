---
title: "startx always?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by jeremygjohn on 2008-04-28
Ok if i use start GDM i get to login screen but says i cantl login as root but i started it with root lol.. If i use startx i get to desktop and it says i have root but then i cant access users and groups says i dont have access i did whoami command and it says root??! 
Secound how do i make it to boot always with startx? so i dont have to go to recovery shell to do it..

---

### Post by kerry_s on 2008-04-28
in ubuntu you don't use root, it's setup to use sudo, programs are reworked to use sudo. sudo is alot safer. trying to use root will break ubuntu.

debian uses root & users if you want to go there. it's also alot easier to setup auto log in with out a log in manager.
net installer->
[http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso)

personally, i think you should learn to use sudo. i use debian but i lock root and use sudo. with a root account your security is only half, they already know your user and just have to crack your password.

---

### Post by Pumalite on 2008-04-28
This might help:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

