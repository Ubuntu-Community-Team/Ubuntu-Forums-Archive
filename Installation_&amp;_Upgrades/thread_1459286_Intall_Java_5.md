---
title: "Intall Java 5"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by zeez on 2010-04-21
Hello,

How do i install java4 on ubuntu?


> sudo apt-get install sun-java4-bin sun-java4-jre
sudo apt-get install sun-java4-jdk


These no longer work...

I already have java6, but i need java4 to run old software

---

### Post by Sef on 2010-04-21
Click [here]("http://java.sun.com/products/archive/").

---

### Post by zeez on 2010-04-21
> **Sef said:**
> Click [here]("http://java.sun.com/products/archive/").

i already did that, and the "fakeroot make-jpkg" trick to create an deb package and it does not work

[http://www.debian-administration.org/articles/142](http://www.debian-administration.org/articles/142)



> andrew@andrew-desktop:~/Desktop$ sudo dpkg -i sun-j2re1.4_1.4.2+19_i386.deb
Selecting previously deselected package sun-j2re1.4.
dpkg: regarding sun-j2re1.4_1.4.2+19_i386.deb containing sun-j2re1.4:
 xulrunner-1.9.1 conflicts with j2re1.4
  sun-j2re1.4 provides j2re1.4 and is to be installed.
dpkg: error processing sun-j2re1.4_1.4.2+19_i386.deb (--install):
 conflicting packages - not installing sun-j2re1.4
Errors were encountered while processing:
 sun-j2re1.4_1.4.2+19_i386.deb
andrew@andrew-desktop:~/Desktop$ 

i also did this and the error continues 

> sudo apt-get autoremove xulrunner


---

### Post by zeez on 2010-04-21
update, the conflict continues on a "virgin" ubuntu machine

---

