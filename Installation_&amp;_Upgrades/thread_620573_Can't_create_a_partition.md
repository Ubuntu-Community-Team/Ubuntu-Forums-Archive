---
title: "Can't create a partition"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by TV-VCR on 2007-11-22
I get this with the installer:

[[IMG]http://img248.imageshack.us/img248/6489/screenshot3og0.th.png[/IMG]](http://img248.imageshack.us/my.php?image=screenshot3og0.png)

And I get this with the built-in partition (Gparted):
[[IMG]http://img248.imageshack.us/img248/208/screenshot5ew1.th.png[/IMG]](http://img248.imageshack.us/my.php?image=screenshot5ew1.png)]

Why??? Drive is Seagate barracuda 7200 (or something) RPM, 500 GB, SATA 3.0 :mad:

---

### Post by taurus on 2007-11-22
Why don't you post a screenshot of gparted?

---

### Post by TV-VCR on 2007-11-22
> **taurus said:**
> Why don't you post a screenshot of gparted?

What? The second is Gparted.

Oh, and is it possible the boot loader needs to go in a different area? Currently it's going to the "hd0" device. I have 3 hard drives.

---

### Post by taurus on 2007-11-22
You have two windows blocking the actual gparted screen!  Otherwise. post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by TV-VCR on 2007-11-22
> **taurus said:**
> You have two windows blocking the actual gparted screen!  Otherwise. post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70841fad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70841faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         124      995998+   5  Extended
/dev/sdb2             125       23622   188747685   83  Linux
/dev/sdb5               1         124      995967   82  Linux swap / Solaris

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64061985

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91202   732571648    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by taurus on 2007-11-22
Go ahead and install it and when you get to the partition part, click the Manual and tell the installer to mount /dev/sdb2 as root, /, and /dev/sdb5 as swap.  Don't forget to put a check in the format window to format /dev/sdb2.

---

### Post by TV-VCR on 2007-11-22
> **taurus said:**
> Go ahead and install it and when you get to the partition part, click the Manual and tell the installer to mount /dev/sdb2 as root, /, and /dev/sdb5 as swap.  Don't forget to put a check in the format window to format /dev/sdb2.

It still fails with that error message.

---

### Post by TV-VCR on 2007-11-22
Oh... my... god...

It actually works! Nevermind then.  :popcorn:

---

