---
title: "[SOLVED] Problem Installing Ubuntu with Windows - Dual Boot"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by RonB123123 on 2006-11-14
Problem Installing Ubuntu with Windows - Dual Boot

Everytime I install Ubuntu, 6.06 or 6.10, and I already have Windows installed, Ubuntu ends up killing Windows.

I know I'm doing something wrong. At the last step of installing Ubuntu 6.06/6.10, it asks to partition the drive. And each time I give it 50 GB out of my 150 GB hard drive. 

Is that what I'm doing wrong? I read some articles of installing ubuntu, but they aren't any help toward my problem.

---

### Post by ReaderRat on 2006-11-14
Partitioning - ReSize a dual-boot system
          [http://www.ubuntuforums.org/showpost.php?p=1642649&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1642649&postcount=2)
[**Dual-Booting (One HDD)**](http://users.bigpond.net.au/hermanzone/)

---

### Post by RonB123123 on 2006-11-15
Hey ReaderRat, I found out I do still have Windows on my computer but I can't access it. There is an option in grub for Windows Home Edition. When I select it, I get an error message saying Windows could not be loaded.

Is there any way for me to get a hold of my Windows HD? Thank you.

---

### Post by ReaderRat on 2006-11-15
run this in the Terminal and post the results please:
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

---

### Post by RonB123123 on 2006-11-15
Here are the results. 

for "cat /etc/fstab"

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d1c6e184-e927-4203-b7c0-1a45db218882 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=cbbff5c0-93fa-4163-8e70-3c25ad69b649 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0


and for "sudo fdisk -l"

> 
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         549       11117    84895492+   7  HPFS/NTFS
/dev/sda2               1         548     4401778+   b  W95 FAT32
/dev/sda3           11118       24137   104583150   83  Linux
/dev/sda4           24138       24321     1477980    5  Extended
/dev/sda5           24138       24321     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order


Reply back soon. Thanks.

---

### Post by RonB123123 on 2006-11-16
ReaderRat or someone, please help me.

---

### Post by RonB123123 on 2006-11-17
Anybody??? ](*,)

---

### Post by geek_Man on 2006-11-17
Sorry, Ron. You don't have Windows on your computer anymore. When you tell it to take 50 GB of the 150 GB partition, you're reformating that partition, so Windows is gone (whether that's a good thing or bad thing... I'm not really sure ;) ). GRUB still has Windows in the menu 'cause menu.lst hasn't been changed. When you reinstall Windows tell it to only use 100 GB. Sorry that's the only help I can give.

---

### Post by confused57 on 2006-11-17
Before you reinstall Windows, you can try repairing your mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

What you're doing is booting with the Windows install cd, press "r" for recovery, then enter **fixmbr** to repair...your Windows should boot if the Windows partition hasn't been corrupted.
   If you can establish that your Windows will boot, you can try reinstalling grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

It's kind of a roundabout way, but it'll let you know if your Windows is still intact.

---

### Post by ReaderRat on 2006-11-18
I'm sorry to keep you hanging, Ron. I was running an unstable version of Ubuntu, and it crashed and took the Internet with it. I am just now back on line.
If your Windoze partition is hosed, the way to re-install is to load Windoze back first and at the partitioning point, allocate half of the harddisk to Windoze and leave the other half unallocated for Ubuntu. You can partition it when you install Ubuntu. Here are some links:
[**Partitioning (XP & Ubuntu)**](http://psychocats.net/ubuntu/partitioning)
[**Installing Ubuntu**](http://www.psychocats.net/ubuntu/installing)

---

