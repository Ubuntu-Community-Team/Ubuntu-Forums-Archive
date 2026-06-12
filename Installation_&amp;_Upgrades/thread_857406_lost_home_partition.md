---
title: "lost home partition"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by paul555 on 2008-07-12
Hi all i just installed ubuntu 8.04 in my pc and i wanted to use an old home partition i had in the past.My problem is that when i try to mount it i get this error :
```
# mount -t reiserfs /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Is there a way to at least save some data from the partition?

---

### Post by ajgreeny on 2008-07-12
First you need to use sudo in front of the command as it can only be used with root permission.  Have a look at [this]("https://help.ubuntu.com/community/RootSudo") to read all about **sudo**
However as this is your /home partition you need to have a look at [this]("http://www.psychocats.net/ubuntu/separatehome") or reinstall and use manual partitioning when you get to that part and make sure you set sda2 as /home, but also make sure you don't format it in the install procedure.

---

### Post by paul555 on 2008-07-12
The command i run it with root permission:
```
root@:~# mount -t reiserfs /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Now i wonder if it is possible to mount the partition and recover some data from it.

---

### Post by jerome1232 on 2008-07-12
just curious what's the output of

```
sudo fdisk -l
```

---

### Post by paul555 on 2008-07-12
```
root@:~# sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c5d7b87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29665   238284081   83  Linux
/dev/sda2           29666       30515     6827625   83  Linux

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x364828a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6502    52227283+   7  HPFS/NTFS
/dev/sdb2            6503        9797    26467087+  83  Linux
/dev/sdb3            9798        9964     1341427+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75168b04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdc2            2551       38913   292085797+   7  HPFS/NTFS
```

---

### Post by jerome1232 on 2008-07-12
There's you're problem /dev/sda2 has an id of 83 which is an ext3 filesystem

---

### Post by paul555 on 2008-07-12
Well i tried with ```
root@:~# mount -t ext3 /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
``` but still no luck :( .Is there a way to fix this?

---

### Post by jerome1232 on 2008-07-12
You know what I apologize i miss read my own output I thought my reiserfs was showing an ID of 5 but that's my extended partion, the reiserfs is show 83 just like my ext3 partions. So I was wrong. Maybe open up gparted and run a check on it, ```
sudo reiserfsck --yes --fix-fixable /dev/sda2
``` would be the cli equivalent of that. That's about as far as I could help.

---

### Post by paul555 on 2008-07-13
I managed to sole this executing the following :
```
fsck.reiserfs  /dev/sda2
```
```
reiserfsck --rebuild-tree /dev/sda2
```
```
mount -t reiserfs /dev/sda2 /mnt/
```

---

