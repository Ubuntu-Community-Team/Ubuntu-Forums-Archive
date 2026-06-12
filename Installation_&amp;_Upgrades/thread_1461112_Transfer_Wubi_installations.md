---
title: "Transfer Wubi installations"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by cmpgm88 on 2010-04-23
Hello!
 
I will be getting a new computer soon, and I would like to transfer Wubi partitions from one computer with Windows to another. (The reason I want to transfer the partitions instead of just making a new installation is because I want to keep **_EVERYTHING_** intact and all the files/settings/applications/etc the same.)
 
Thanks!
 
-cmpgm88

---

### Post by bcbc on 2010-04-24
By partitions you mean the wubi file on Windows that contains ubuntu i.e. c:\ubuntu\disks\root.disk (this file contains the file system with Ubuntu on it, that's loop mounted whenever you boot into Ubuntu).

So, all you do is install wubi on the new machine, and then replace the new root.disk file with the old one.

---

### Post by cmpgm88 on 2010-07-09
> **bcbc said:**
> By partitions you mean the wubi file on Windows that contains ubuntu i.e. c:\ubuntu\disks\root.disk (this file contains the file system with Ubuntu on it, that's loop mounted whenever you boot into Ubuntu).

So, all you do is install wubi on the new machine, and then replace the new root.disk file with the old one.

Ahh!  Thanks!!!

---

### Post by bcbc on 2010-07-10
I should have mentioned that you might run into issues if you have e.g. a proprietary graphics driver on the one computer but a different graphics card on the new one. Or if the old one is running 64-bit ubuntu and the new machine is 32-bit (the other way round is ok). 

Generally ubuntu is pretty good moving from one machine to another, except for the above. I've moved wubi and other installations (on external drives) between computers with no issues.

---

