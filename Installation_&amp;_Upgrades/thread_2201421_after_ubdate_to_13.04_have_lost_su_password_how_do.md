---
title: "after ubdate to 13.04 have lost su password how do i get it back"
date: 2014-01-24
forum: Installation &amp; Upgrades
---

### Post by unixisit on 2014-01-24
I have receved an automatic update then lost my su password. try to go back to recovery but it semes to be lost is ther a solution?

---

### Post by dargaud2 on 2014-01-24
On a normal install there is no *su*, only *sudo* which uses YOUR password (does this work? If so do 'sudo passwd' to change it). In case you configured you system to have a valid super user and you forgot the password (I doubt any kind of update would touch that), then simply boot with a livecd, mount you main drive and then edit the 2nd field of /mnt/etc/shadow to change the password. For instance copy the one of the user and then change it with the passwd command once you are logged in.

---

