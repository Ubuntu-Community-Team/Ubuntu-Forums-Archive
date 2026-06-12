---
title: "[PICS] Simple installation questions"
date: 2005-09-16
forum: Installation &amp; Upgrades
---

### Post by heredago on 2005-09-16
I have one 250GB HD as master.
WinXP has been installed on it for some time (NTFS).
Using Partition Magic, I resized the only partition (NTFS) so I could have 11.4 GB of free space.

I want to dual boot WinXP & Ubuntu.
I don't want to use the "Automatically partition the free space" function because once for all, I want to **understand** the concept!

I only want to know how to create a 1.4 GB partition of swap and a 10.0 GB ReiserFS partition.


[B]Swap area= primary or logical??, "bootable flag" off-on??
ReiserFS partition= primary or logical??, "bootable flag" off-on??[/B]


Thank you!


[IMG]http://img378.imageshack.us/img378/852/10tv1.jpg[/IMG] 

[IMG]http://img378.imageshack.us/img378/8067/27uy.jpg[/IMG] 

[IMG]http://img92.imageshack.us/img92/1148/37oc.jpg[/IMG] 

[IMG]http://img378.imageshack.us/img378/5863/42gn.jpg[/IMG] 

[IMG]http://img378.imageshack.us/img378/5922/65jp.jpg[/IMG]

[IMG]http://img378.imageshack.us/img378/8067/27uy.jpg[/IMG] 

[IMG]http://img378.imageshack.us/img378/5863/42gn.jpg[/IMG] 

[IMG]http://img291.imageshack.us/img291/6263/86ks.jpg[/IMG]

---

### Post by Tym_The_Enchanter on 2005-09-16
Hi heredago,

You can basically use the default options for the partitions during the install without any problems, swap will have very few options any way. For your ReiserFS partition you can leave the bootable flag as false and create it as either a logical or primary partition, may as well create it as primary if you only have a single windows partition.

On a side note you may (or may not) have a problem booting Ubuntu if your new partition is at the end of the disk as SOME BIOSes require that the boot image is installed in the first part of the disk (I forget the exact limit). Hopefully this won't happen and you'll be fine. If it does then you'll need to play around with partition magic and create a small (250MB or so) partition near the begining of the disk. I think Partition Magic has more info on this.

---

