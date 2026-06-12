---
title: "NTFS Partition"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by vanishedsoul on 2006-10-14
hi! 

i'm a beginner and want s to install UBUNTU, but i have some queries, may be someone can help me here...ok

i already have windows xp professional in my C: drive (with file system ntfs) and want to have it along with my UBUNTU.

First i make another partition of ntfs lets suppose D: and i install UBUNTU there, will it be competible with the ntfs file system? 

Incase i install the UBUNTU, will it format my whole hard disk or just the partision where i'm going to install it?

The new partision where i'm going to install UBUNTU lets say D:, do i have to make it the primary one, also i'm having winxp on C: and i also want to keep it.

After installing UBUNTU, will it automatically add my other OS (windows xp pro) in the boot menu or i have to do some thing else?

i'm really very curious to install UBUNTU, so please do help me,..... thanks

---

### Post by taurus on 2006-10-14
Yes, you need to have an empty partition before you install Ubuntu and Ubuntu will use it own filesystem, most likely ext3.  And if you install GRUB (bootloader) in MBR, then you can boot either Ubuntu or XP when you turn on your computer.  In fact, you can even access your NTFS in Ubuntu...  Just make sure you tell the installer which partition you want to install Ubuntu!!!

---

### Post by kidders on 2006-10-14
Hi there,

Installing Ubuntu on a Microsoft filesystem (ie one that has crappy permissions support) is **absolutely not recommended**, although there's nothing stopping you in theory.

Ubuntu shouldn't make any changes to your system without asking first, but backups are always a good idea!

---

### Post by vanishedsoul on 2006-10-14
ok, so i need a sepaerate partitions ( aprimary one?) to instal UBUNTU. Ok, then i have to make another partiotn with the partition tool present in the UBUNTU live cd with the format of ext3??? 

also do i need a swap partions and a shared fat32 partition for sharing the files with xp and ubuntu, coz i have read about these swap and fat32 partitions here...
[http://www.crhc.uiuc.edu/%7Emjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/%7Emjmille2/howtos/dual-boot-linux-and-windows/)

---

### Post by aysiu on 2006-10-14
Read this:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by kidders on 2006-10-14
Hey again,

Ubuntu's partition(s) don't need to be primary ones. It's not very fussy. You can make your partitions with any tool you like, but you'll have to use one from Linux to *format* them, since Microsoft only supports its own filesystems. You can create partitions during Ubuntu's setup, or format pre-existing ones.

There's no particular reason to choose ext3 over any other (decent) filesystem ... the choice is yours :-)

> do i need a swap partions and a shared fat32 partition
You don't _need_ either, but having said that...

[LIST]
[*]No operating system will work terribly well without any virtual RAM.
[*]Some way of exchanging files between all your operating systems is very convenient. If you don't want to use FAT32 (I certainly wouldn't!), you can always teach Windoze to read Ext2 filesystems.
[/LIST]

As aysiu indicates, all this information is freely available elsewhere, in far more detail than we can provide.

---

### Post by vanishedsoul on 2006-10-14
thanks guyzz, it wa really very helpful, but i still got a bit of confusion. The drive which on which i'm going to instal ubuntu, which format it should have??ext2, ext3, or anyother??

---

### Post by taurus on 2006-10-14
ext3 for your Linux and swap for your swap partition.

---

### Post by kidders on 2006-10-14
You have a range of choices, however ext3 is perhaps the most common. For practical reasons, avoid anything designed by Microsoft, though.

---

