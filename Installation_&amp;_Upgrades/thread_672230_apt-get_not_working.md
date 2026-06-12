---
title: "apt-get not working"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by divali on 2008-01-19
Trying to reinstall automatix after the recent xorg update fiasco and allIgot was:

 ImportError: No module named operator
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Selecting previously deselected package automatix2.
Unpacking automatix2 (from .../automatix2_2.0.6-7.10gutsy%5fi386_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/restricted-manager_0.33.1_all.deb
 /var/cache/apt/archives/gdebi_0.3.2ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
divali@ubuntu:~$ 

Can some one tell me what is wrong and how to fix apt-get. I would be very grateful.

---

### Post by aysiu on 2008-01-19
Automatix has been a bit finicky of late (other people have had problems installing it because of some Tango icon theme dependency). You may get better help at the Automatix Forums:
[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

---

### Post by divali on 2008-01-19
Thanks. This xorg update is causing me loads of problems, apt-get, java applets gone, apt-get playing up. gdebi wont work, aptitude wrecked, etc etc. To name just a few.
But, hey at least I've got a working system with an internet connection.

---

