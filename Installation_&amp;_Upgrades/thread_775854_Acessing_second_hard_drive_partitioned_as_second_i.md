---
title: "Acessing second hard drive partitioned as second installation"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Adsrhodes on 2008-04-30
Hi,

I Recently had a bit of trouble that cropped up while updating from 7.10 to 8.04. So I could get onto the web and get advice to solve the problem (which I did, thanks everyone!) I plugged in an old SATA 80Gb drive and installed a completely fresh copy of Ubuntu 7.10, fir internet and the like. I have decided to keep it on there, just in case I mess up again! 

However, in both of my installations of Ubuntu, I cannot access the other's drive at all. I simply get a permissions denied message. Any ideas how I can fix this?

---

### Post by El King on 2008-04-30
is it mounted or not ?!
open terminal and write
```
sudo fdisk -l
```
and post back results

---

### Post by Adsrhodes on 2008-04-30
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008d376

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59572   478512058+  83  Linux
/dev/sda2           59573       60801     9871942+   5  Extended
/dev/sda5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ba408

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9553    76734441   83  Linux
/dev/sdb2            9554        9964     3301357+   5  Extended
/dev/sdb5            9554        9964     3301326   82  Linux swap / Solaris


When I right click on the second drive, it offers an option to mount, but I again get a permission denied pop up.

---

