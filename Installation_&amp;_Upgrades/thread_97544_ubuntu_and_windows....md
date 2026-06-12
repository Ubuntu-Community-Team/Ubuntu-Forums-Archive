---
title: "ubuntu and windows..."
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by Tummas on 2005-12-01
Is it possable to have ubuntu and windows innstalled on a pc at the same time?

---

### Post by Pablo_Escobar on 2005-12-01
Without a problem. If You'll install Ubuntu it will (in 99% of cases) detect the Window$ at add it to grub.
At boot time You will have an option to select what do You want to use. (Ubuntu or Window$)

---

### Post by Tummas on 2005-12-01
ok, but i tryed using expert installation, i just couldn't figure it out... :( 
can i just use default innstall?

---

### Post by Pablo_Escobar on 2005-12-01
Yes, If You're a beginner in the Linux world then use the default install (much easier)

---

### Post by Topsiho on 2005-12-01
**Be sure you don't reformat the partitions that Windows is using.**

If you reformat those your Windows has gone to, I almost said, but I am not going to say so :)

So please be very careful when doing the partition part of the installing that you Identify the Windows partitions correctly. /hda1 is (almost?) always the C:\ drive with the Windows OS on it. If you have other Windows drives check first their dimensions (how many GB), in order to be able to identify them.

Usually one can identify the Windows drives by the type of the partitions they are on, such as Win95, but maybe the partitions you are going to use for Linux and used to contain Windows drives are still Win95 or so.
Then the type should be changed to ext2, ext3, reiferfs or so (ext3 and reiserfs are logging files and I think you should prefer using one of these).
You need to create a swap partition too, reserve a small partition, about twice the internal memory in your computer)

I also advise you to create a (roomy) /home partition, in which come the personal files. Which you are NOT going to reformat a next install.

Success,

Topsiho

---

### Post by aysiu on 2005-12-01
This tutorial explains everything:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by towsonu2003 on 2005-12-01
and please make backups before trying to install...

---

