---
title: "grub problems"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by [z]er0 HP on 2008-04-07
Well basically I've been using linux for about 2 months now and i recently got a new hard drive so i wanted to allocate about 60gb for a new windows partition and about 420gb for linux storage. After i installed windows it removed grub from my MBR and now i'm up **** creek.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe454e454

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000db36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       50993   409601241   83  Linux
/dev/sdb2           50994       60800    78774727+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b559b55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       13995   112414806   83  Linux
/dev/sdc2           13996       14593     4803435    5  Extended
/dev/sdc5           13996       14593     4803403+  82  Linux swap / Solaris

```

sda is a windows partition and its basically full of useless windows crap.
sdb is my newest hard drive which i have partitioned for linux storage and a small part for windows.
sdc is where ubuntu is installed and as far as i know where grub is installed.

I have seen many tutorials where it says i should 'sudo grub' and then find etc etc
```
grub> find /boot/grub/stage1 
 (hd2,0)

```
```
grub> root (hd2,0)

```
```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd2,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

```

Basically i need to know where i've gone wrong and what i need to do
Forgot to add, A quick response would be greatly appreciated, I need to get back to real linux not this livecd.

---

### Post by [z]er0 HP on 2008-04-07
another addition:
The reason I've tried to reinstall grub is that when i turn on my computer it says
```
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 15

```

---

### Post by zvacet on 2008-04-07
[Here](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by [z]er0 HP on 2008-04-07
Thanks, some information i found at that link worked a charm.
Super GRUB disk is great!

---

