---
title: "How can I remove old packages after update?"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by alvonsius on 2006-06-09
Hi all, I have upgrade all my system to Dapper now. But when I take a look at my disk space it seems the upgrade process itself eats a lot of space. When I look at the /var/cache/apt/archive I found the old packages and the new packages in that same directory (ie. libuniconf4.2_4.2.2-1ubuntu1_i386.deb and libuniconf4.2_4.2.2-1ubuntu2_i386.deb). How can I remove the old one (i.e the libuniconf4.2_4.2.2-1ubuntu1_i386.deb) , so the only one left is the new packages (i.e libuniconf4.2_4.2.2-1ubuntu2_i386.deb). And is there any negative effects by doing this?

TIA

---

### Post by Dr. Nick on 2006-06-09
[quote=alvonsius]Hi all, I have upgrade all my system to Dapper now. But when I take a look at my disk space it seems the upgrade process itself eats a lot of space. When I look at the /var/cache/apt/archive I found the old packages and the new packages in that same directory (ie. libuniconf4.2_4.2.2-1ubuntu1_i386.deb and libuniconf4.2_4.2.2-1ubuntu2_i386.deb). How can I remove the old one (i.e the libuniconf4.2_4.2.2-1ubuntu1_i386.deb) , so the only one left is the new packages (i.e libuniconf4.2_4.2.2-1ubuntu2_i386.deb). And is there any negative effects by doing this?

TIA[/quote]

the cache just holds the downloaded packages and can be cleareed. run
sudo apt-get clean
to erase the old files. The program files were updated but the .deb are still their incase you want to reinstall later without redownloading them

quote from apt-get manual

> **clean** clean clears out the local repository of retrieved package files. It removes everything but the lock file from */var/cache/apt/archives/* and */var/cache/apt/archives/partial/*. When APT is used as a **dselect**(8) method, clean is run automatically. Those who do not use dselect will likely want to run apt-get clean from time to time to free up disk space.

---

### Post by alvonsius on 2006-06-10
*sob* ... the clean option surely deleted the packages, ALL of them *sob*

after reading the manual again, I found out about "autoclean" option ... should have used this instead of "clean" ...

but thanks anyway ... cleaned 1.3GB from my disk :D

---

