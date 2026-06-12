---
title: "Installing server apps after desktop"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by dc52317 on 2007-03-02
I keep getting this error when I try to add server apps (LAMP) via

sudo apt-get install ubuntu-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-server

I just go to the terminal to do this correct? I also did

sudo apt-get update first.
I just want to install the server apps

---

### Post by zvacet on 2007-03-03
System>help>system documentation>ubuntu server guide>package managment>aptitude
**Read it before you start do anything**
```
sudo apt-cdrom add
```
```
sudo aptitude
```
click on search and type lamp server or just list packages that are not install

---

