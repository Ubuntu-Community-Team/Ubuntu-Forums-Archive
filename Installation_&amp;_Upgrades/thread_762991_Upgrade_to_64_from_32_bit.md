---
title: "Upgrade to 64 from 32 bit?"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by midna on 2008-04-22
My computer science department at my school has a student run Ubuntu server that we use a lot. Well, we need more memory and unfortunately 32-bit ubuntu doesn't support large amounts of memory. The server is 2 dual core xeons that are 64-bit and we currently are running ubuntu 32-bit since it was easier to set up at the time.

So is there an "easy" way (read not complete reinstall) to upgrade/install 64bit ubuntu from a 32-bit? 

cat /proc/version
Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 UTC 2007

---

### Post by martrn on 2008-04-22
Ubuntu amd64 bit reposotories are maintained seperate to i386 reposotories and hence ubuntu amd64 or ubuntu i386 is sort of a diffrent distribution.  The codebase for 32 and 64 bit versions will be changed in sorce code at various point to optimise or utilise the diffrence between the diffrent archtecures.

> **midna said:**
> 
So is there an "easy" way (read not complete reinstall) to upgrade/install 64bit ubuntu from a 32-bit? 


No.  There is no "easy way" to upgrade.

You are seriously reccommend to completely back-up your data when makeing the transformation from intel32 bit to amd64bit, and ensure your backup is sucsfull before attempting to install.

---

### Post by midna on 2008-04-23
:( That really sucks.

---

