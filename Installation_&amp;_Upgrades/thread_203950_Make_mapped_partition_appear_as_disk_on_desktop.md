---
title: "Make mapped partition appear as disk on desktop?"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by codified on 2006-06-26
Hi,

I installed Ubuntu on a Dell M80 laptop today, and can now boot into the Ubuntu desktop.  The machine is a dual boot with XP.

The install has magically added two hard disk icons to the desktop - one called DellUtil and the other /dev/sda2.  One is a Dell partition, the other is XP's NTFS partition.

At install I created a FAT32 partition (sda5) to use to exchange files between XP and Linux.  My /etc/fstab maps /dev/sda5 to /windows, and I can see the contents of that folder (partition) using the Ubuntu file explorer.  

I would love to have that partition appear as a 'drive' on the desktop, just like the DellUtility and /dev/sda2 already on the desktop.  Can anyone tell me how to do it?

Thanks!

---

### Post by bikeboy on 2006-06-26
Not sure if this will do it or not but try System > Admin > Disks: Click on the partition and click enable if it's not already.

---

### Post by codified on 2006-06-26
Think it's already enabled.

---

