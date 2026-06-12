---
title: "installation not detecting partition..."
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by sitric on 2007-05-20
i am trying to install fiesty fawn on my machine. i have two HDDs and the one i want to install ubuntu on is hdb... now there is a 30GB NTFS partition in the latter part of the HDD, leaving around 8GB  in the beginning..

the problem is, that when i try to install ubuntu, it doesnt recognize any previous partitition on  hdb. If i run gparted, it also doesnt show me anything on hdb (and tells me that it is unallocated) ... all the ntfs volumes of hda are shown just fine...

so how do i install ubuntu on the 8GB free space? i want to keep my older partition as it is.

PS: that 30GB partition is visible under winxp. i've installed ubuntu before, but have never had a problem like this.

Please help me.

PS2: i just realized that the 30 GB partition on hdb can be mounted and accessed from the livecd.. but it is not recognized by the partitioner...... why?

---

### Post by lw5 on 2007-05-20
Can you post what you get if you type: sudo fdisk -l

---

### Post by sitric on 2007-05-20
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1299    10434186    7  HPFS/NTFS
/dev/sda3            1300        9729    67713975    f  W95 Ext'd (LBA)
/dev/sda5            1300        3701    19294033+   7  HPFS/NTFS
/dev/sda6   *        3702        5052    10851876    7  HPFS/NTFS
/dev/sda7            5053        6222     9397993+   7  HPFS/NTFS
/dev/sda8            6223        9729    28169946    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1170     9397993+   7  HPFS/NTFS
/dev/sdb2            1171        4866    29688120    7  HPFS/NTFS

--------------------------------------------------------------------------------------------------------

i was just trying to install ubuntu using wubi on sdb1 i think...

---

### Post by sitric on 2007-05-20
ok, now i uninstalled wubi.. deleted the ntfs partition. and now i get this...


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1299    10434186    7  HPFS/NTFS
/dev/sda3            1300        9729    67713975    f  W95 Ext'd (LBA)
/dev/sda5            1300        3701    19294033+   7  HPFS/NTFS
/dev/sda6   *        3702        5052    10851876    7  HPFS/NTFS
/dev/sda7            5053        6222     9397993+   7  HPFS/NTFS
/dev/sda8            6223        9729    28169946    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1171        4866    29688120    7  HPFS/NTFS




and still gparted shows sdb as "unallocated"...

---

### Post by sitric on 2007-05-20
*****bump*****

---

### Post by lw5 on 2007-05-21
Hey, what happened between the first and the second post? In the first you have a small ntfs partition as /dev/sdb1 and in the second /dev/sdb2 from the first became /dev/sdb1 (suggesting that indeed, a part is unallocated and should be allocated)

---

### Post by sitric on 2007-05-21
wtf? but i deleted the first partition..
how the hell did the sdb2 become sdb1??? 

is there anyway to correct this?
also, i didnt really get what you just said... the techy part...

---

### Post by monti on 2007-05-25
You can probably work around your problem by using TestDisk, look here: [http://ubuntuforums.org/showthread.php?p=2486121#post2486121](http://ubuntuforums.org/showthread.php?p=2486121#post2486121) 

The bug is located in gparted's subsystem, libparted: [http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14](http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14)

---

### Post by sitric on 2007-05-25
hey i used that testdisk tool... it totally screwed my MBR...
although i think i backed it up... how do i restore it?

i havny touched the HDD with anything, no reformatting, nothing,.... just the MBR.. how can i restore it?

---

### Post by bigngamer92 on 2008-02-16
Same Problem here...

I only have one HDD but Ubuntu (and Kubuntu) do not recognize my WinXP partition.  I don't want to accidentally screw up my XP Partition.  Does anybody know how to fix this problem? I am using 7.10 Live CD

PS: I have a 250GB HDD With Windows  taking up most of that but it has another partition that is associated to Windows. Neither is found.

---

