---
title: "can't install Java Runtime Environment (JRE) 6"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by Pyro_Killer on 2007-03-23
I have installed a whole lot of software the last 72 hours, but there is one software that won't install.  Java Runtime Environment (JRE) 6. I have followed the guide, but the 

fakeroot make-jpkg jre-6-linux-i586.bin

won't work, it can't recognise fakeroot, plz help

---

### Post by depu on 2007-03-23
Have you installed fakeroot before running that command ?

maybe u need to do a sudo apt-get install fakeroot

---

### Post by zvacet on 2007-03-23
Get it from Automatix.

---

### Post by tuga on 2007-03-24
sudo apt-get install sun-java6-jdk

---

### Post by kerry_s on 2007-03-24
Use synaptic and turn on all the repos. Sun-java6 is in the multiverse repos.

---

### Post by tassoman on 2007-03-24
```
apt-get install sun-java6-jre
``` is giving me dependences: **sun-java6-bin** and **ia32-sun-java6-bin**

---

### Post by kerry_s on 2007-03-24
Yes that's right, sun-java is not a small install and you need all of it to work, you need the plug in one if you want to use it in your browser.

---

