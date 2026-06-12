---
title: "How to install mysql n php"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by Cool Surfer on 2007-09-09
I am trying to install mysql and php, but get this error.
=
why@why-desktop:~$ sudo apt-get install mysql
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mysql
why@why-desktop:~$ sudo apt-get install php
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package php

============

Any suggestion pl

---

### Post by pheeror on 2007-09-09
Command-not-found handler could be your friend. Just type php and push enter. But bash completion is definetily your girlmate. ```
. /etc/bash_completion
``` (good to be added to .bashrc)
Now just type aptitude install mysql<tab> or aptitude install php<tab>
Packages you are looking for are  probably 
php5-mysql and libphp-adodb

---

### Post by Cool Surfer on 2007-09-09
Its so simple :D  :guitar::guitar::guitar:

---

