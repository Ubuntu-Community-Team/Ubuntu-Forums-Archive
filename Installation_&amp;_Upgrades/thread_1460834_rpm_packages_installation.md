---
title: "rpm packages installation"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by Ashish Asolkar on 2010-04-23
I want to install rpm packages.
If i use     **rpm -i <package name>** then it gives error as
[B]The program 'rpm' is currently not installed.  You can install it by typing:
sudo apt-get install rpm
You will have to enable the component called 'main'
bash: rpm: command not found
[/B]
but when i go for **sudo apt-get install rpm** then it gives as
[B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rpm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rpm has no installation candidate[/B]

How it can be possible?
and how to install exel.deb packages?
when it gives error as **Error: Dependency is not satisfiable: axel**

Thanx:popcorn:

---

### Post by bumanie on 2010-04-23
You first have to convert the .rpm to a .deb There is a program called alien that can do this, with often, but not always good results. You can get alien [here]("http://www.icewalkers.com/Linux/Software/57020/Alien.html") or alien with a gui [here]("http://linux.softpedia.com/get/System/Software-Distribution/Alien-GUI-10165.shtml") There will be tutorials around to tell you how to do it. Good luck.

---

### Post by oldos2er on 2010-04-23
> **Ashish Asolkar said:**
> I want to install rpm packages.
If i use     **rpm -i <package name>** then it gives error as
[B]The program 'rpm' is currently not installed.  You can install it by typing:
sudo apt-get install rpm
You will have to enable the component called 'main'


Go to menus System, Administration, Software Sources, and make sure all repositories are enabled. The error is telling you the 
'main' repository is currently disabled.

---

