---
title: "No Global Menu Libreoffice 4.01"
date: 2013-03-17
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2013-03-17
Purged Libreoffice 3.6 and installed Libreoffice 4.01 via official debs from website.  Do not have global menu, tried to install lo-menubar and here is the output:

henry@hewjr:~$ sudo apt-get install lo-menubar
  Reading package lists...
 Done  Building dependency tree         Reading state information... Done
  Some packages could not be installed.
 This may mean that you have  requested an impossible situation or if you are using the unstable  distribution that some required packages have not yet been created  or been moved out of Incoming.  The following information may help to resolve the situation:
   The following packages have unmet dependencies:   lo-menubar : Depends: libreoffice-gtk but it is not going to be installed
  E: Unable to correct problems, you have held broken packages.
  henry@hewjr:~$

I assume that I am not going to be able to setup global menu with 4.01.  Libreoffice 4.0 ppa is currently in a no publishing status, and only has 4.01 rc2 available.  What are my options.

Henry

---

### Post by dino99 on 2013-03-18
use the packages from ubuntu (lo-menubar has been removed a while back)

[https://launchpad.net/ubuntu/+source/libreoffice](https://launchpad.net/ubuntu/+source/libreoffice)

or from that ppa:  [https://launchpad.net/~ricotz/+archive/ppa](https://launchpad.net/~ricotz/+archive/ppa)

---

### Post by Hewjr100 on 2013-03-18
Will do asap.  Thanks

Henry

---

