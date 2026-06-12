---
title: "install nvidia drivers manually"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by ubun2warrior on 2010-09-23
hi

can someone tell me how to install nvidia-linux-x86-256.53.run which i have downloaded from nvidia's website.

i log in as root and so sh  ./NVIDIA-Linux-x86-256.53-pkg1.run 

the installation begins but in the end there is some error saying you have to install without any x session running or something and install it.

plz help..

ubun2warrior

---

### Post by mikewhatever on 2010-09-23
As the error says, xserver should not be running while installing, and there is no need to login as root.

sudo service gdm stop #to stop xserver

sudo ./NVIDIA-Linux-x86-256.53-pkg1.run

---

### Post by ubun2warrior on 2010-09-25
hi 
thanks for replying

instruction given on NVIDIA's website are quiet nice
did the installation acoordingly

regards
ubun2warrior

---

