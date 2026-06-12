---
title: "Update problems python 2.5"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by StarglowOne on 2007-06-18
Hi im trying to update my feisty install, but everytime it is supposed to install the update for python 2.5 the computer lcks up and only way out is to cut the power for the computer. I need to get that installed or i wont be able to update the rest it seem.

when running sudo dpkg --configure -a after reboot i get this message:

> dpkg: fel vid hantering av python2.5 (--configure):
 Paketet är i ett väldigt dåligt inkonsistent läge - du bör
 ominstallera det innan du försöker konfigurera.
Fel uppstod vid hantering:
 python2.5

badly translated to:
> 
dpkg: error when managing of python2.5 (--configure):
 The package is in a very bad inconsistency state - you should reinstall it before you try to configure.
Error arose at management:
 python2.5

But when i go into synaptics and look at python 2.5 i get no alternative to reinstall, only deinstall or update

Any help appreciated, as this drives me nuts

---

### Post by visik7 on 2007-06-18
try aptitude purge python2.5 and then reinstall it

---

