---
title: "Update-autoremove problem...any idea?"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by Kiraitachi on 2012-11-22
Hey guys, im not sure if this is normal but has no sense...when I do sudo apt-get update and then a sudo apt-get dist-upgrade I get to install this packages 

> libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  liborc-0.4-0:i386 libqtwebkit4:i386 libsqlite3-0:i386 libxml2:i386When 

doing sudo apt-get autoremove the same packages will appear as approved for removal....like WTF??? hahaha

> kira@kira-Satellite-A665:~$ sudo apt-get autoremove
[sudo] password for kira: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  liborc-0.4-0:i386 libqtwebkit4:i386 libsqlite3-0:i386 libxml2:i386
0 upgraded, 0 newly installed, 6 to remove and 1 not upgraded.
After this operation, 31.8 MB disk space will be freed.
Any ideas???  Thanks!


Besides as you can see appears 1 not upgraded (just if anyone knows...) thats the skype-bin:i386 package saying it has been kept back...even doing a dist-upgrade cause I already have skype installed...is it worth it to upgrade to skype-bin:i386?? (I have a 64 bit machine, but I think the new skype is general architecture...anyways didnt install it before cause of the skype tray menu not showing with the new version maybe they already fixed it???)

---

### Post by Zteam on 2012-11-22
You can use aptitude (not installed by default) to find out why it want's to install and remove these packages:

Try sudo aptitude why packagename and it will tell why it want to install these packages.

In the same way you can try sudo aptitude why-not packagename to find out why it want to remove this packages.

Cheers. :popcorn:

---

