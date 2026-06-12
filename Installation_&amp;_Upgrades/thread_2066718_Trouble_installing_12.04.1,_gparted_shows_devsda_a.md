---
title: "Trouble installing 12.04.1, gparted shows /dev/sda as unallocated"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by .mouse on 2012-10-05
Here's the situation.  I was dual booting win7 and ubuntu 10.04.  I only use windows for games and because of win7's overhead I figured some games would run smoother under xp so I installed xp over it.  I figured since I was reinstalling windows I should also reinstall ubuntu and bring it up to it's most current LTS, 12.04.1  While booting from the livecd and trying to install it, gparted suddenly shows my entire sda as unallocated and gives the warning: "can't have overlapping partitions".  Running fdisk -l gives this output:

```
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31871   256003776    7  HPFS/NTFS
/dev/sda2           31872       60801   232380163    5  Extended
/dev/sda3           60547       60801     2046976   82  Linux swap / Solaris
/dev/sda5           31872       34421    20480225+  83  Linux
/dev/sda6           34421       60546   209850368   83  Linux

```I'm not very good with reading sectors, let alone knowing how to manually adjust them so would anyone be able to tell me what could be overlapping?  Or if that's not the problem could anyone tell me what is?  I'm currently running ubuntu 10.04 from /dev/sda5(file system partition) and /dev/sda6(home partition) and I'm honestly baffled by this hole situation so any insight or solutions would be great.

---

### Post by Bucky Ball on 2012-10-05
*Thread moved to **Installations & Upgrades***

---

### Post by .mouse on 2012-10-05
Running testdisk /list gives me this output:

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Please wait...
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512
Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512
Disk /dev/sdc - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512
Disk /dev/sr0 - 728 MB / 694 MiB - CHS 355480 1 1 (RO), sector size=2048

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition            Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 31870 254 63  512007552
 2 E extended             31871   1 62 60800 254 63  464760326
 3 P Linux Swap           60546  24 23 60800 237 45    4093952
Space conflict between the following two partitions
 2 E extended             31871   1 62 60800 254 63  464760326
 3 P Linux Swap           60546  24 23 60800 237 45    4093952
   X extended             31871   1 63 34420 172 56   40960452
 5 L Linux                31871   2  1 34420 172 56   40960451
   X extended             34420 172 57 60545 246 53  419702784
 6 L Linux                34420 205 26 60545 246 53  419700736

```

From what I can tell sda5 and sda6 are sharing the same ending and starting sector.  If I'm understanding this correctly my goal would be to move sda5's ending sector to 34419?  Is that actually a good idea or is there some kind of math formula I should use to determine the ending sector for sda5?  In addition is this a task I can trust testdisk with?  Also will doing this cause all data in sda5 to be lost?

---

### Post by coffeecat on 2012-10-05
Put testdisk away for the time being. You probably won't need it and you might make things worse with it. This situation can usually be fixed with another app, but first let's see what your partition layout is like with a better readout of fdisk. The 10.04 version of fdisk gives output in cylinders when you use the -l option, which is of no use. We need output in sectors. Run this from Ubuntu 10.04:

```
sudo fdisk -lu
```

---

### Post by .mouse on 2012-10-05
It seems I was way off.  The real problem was that some how the swap space became both a primary and a logical partition.  I have no idea how that happened but luckily Enyc noticed it before I tried to change any starting or ending sectors.  So I used fdisk to delete it and made a new swap space.  Rebooted and double checked, problem solved and I'm going to be marking this thread as such.

Thank you for replying, Coffeecat.  This thread was quickly becoming a conversation between myself and the people of the future.  ):P

---

### Post by coffeecat on 2012-10-05
Glad you've solved it. For future reference, and depending on the output of fdisk -lu, I had been going to point you to fixparts, although you don't seem to need it now:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

One for your bookmarks! :)

---

### Post by Bucky Ball on 2012-10-05
> **.mouse said:**
>   This thread was quickly becoming a conversation between myself and the people of the future.  ):P

I've had them on here but somehow talking to the forum and reading it back can sometimes help solve the problem!

Good work and enjoy ...

---

