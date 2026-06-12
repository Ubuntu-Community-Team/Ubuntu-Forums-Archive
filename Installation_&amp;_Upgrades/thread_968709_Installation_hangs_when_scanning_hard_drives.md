---
title: "Installation hangs when scanning hard drives"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by redalastor on 2008-11-02
When the Kubuntu install CD (which I tested for integrity before using) reach the step where I should pick where it installs, it shows progress bar about analyzing my disks and then hangs completely. I'm left at the dialog where I can pick the keyboard and both back and forward are disabled.

I have two hard drives, a 160GB (sda) which has Windows XP on it and a 300GB (sdb) which should host Kubuntu.

---

### Post by taurus on 2008-11-02
Before clicking the install icon, can you open a terminal and post the output of this command here regarding harddrives?

```
sudo fdisk -l
```

---

### Post by redalastor on 2008-11-02
sdb used to have partitions but they were deleted. The output of the fdisk -l command seems completely normal to me. Both disks work fine too.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32e132e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19451   156240126    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a209a

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$

```

---

### Post by redalastor on 2008-11-03
Now something really weird happened. I tried to install 3 or 4 times (checking if OEM would do something different, checking if removing partitions would, etc) and it never worked. I tried again after fdisk -l for kicks because it's not supposed to be a command that changes anything and it now works. It seems to be installing.

I really wonder what could cause this weird glitch.

---

