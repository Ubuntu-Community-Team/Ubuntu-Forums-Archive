---
title: "Dual boot problem after reboot from Windows XP"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by da-jay on 2006-07-05
I have a Dell Precision 380 system which has two SATA disks and a Pentium D. WIndows XP is running on disk 1 and now I installed the Ubuntu 64bit version on disk 2. After the installation everything seemed to work OK. I removed the live cd and rebooted into Ubuntu, sofar everything OK. Now I rebooted into Windows, also OK (Windows performed scandisk at startup and I could not stop skip it). However when I tried rebooting again, the system went into a loop: the BIOS screen flashes and than I see GRUB and than again the BIOS screen etc. It seems something messed up my mbr (scandisk maybe)?  

I used the Ubuntu live CD to boot into Ubuntu again. The disks are partitioned as follows:

sda1 -vfat (some small partition created by windows or Dell ??)
sda2 -ntfs (windows XP installation)

sdb1 -ntfs  (second windows partition)
sdb2 -ext3  (linux partition)
sdb5 -swap  (linux swap)

My question now is, how to fix this problem, i.e., how can I get my dual boot to work again as it did right after the installation?

Thanks!

---

### Post by flarkit on 2006-07-05
You could attempt to install Grub by itself from a terminal session on the LiveCD. But that requires having good knowledge of the precise partitioning for XP and Ubuntu.

Considering that you've just installed Ubuntu (hopefully without any tweaks, updates, etc), I'd simply reinstall Ubuntu again. That ***should*** replace Grub too.

---

### Post by da-jay on 2006-07-05
I tried reinstalling Ubuntu several times. Every time the same thing happens as I described. 

Now I ran "fdsik /mbr" from win98SE bootdisk so Windows XP is booting correctly but off course Ubuntu is not bootable now. I use the live CD to get into Ubuntu. But how to make Ubuntu bootable from there and fix my dual boot?

If this helfps in finding a solution ... this is my partition info:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10       19451   156167865    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11116    89289238+   7  HPFS/NTFS
/dev/sdb2   *       11117       19110    64211805   83  Linux
/dev/sdb3           19111       19452     2747115    5  Extended
/dev/sdb5           19111       19452     2747083+  82  Linux swap / Solaris

---

### Post by confused57 on 2006-07-05
Found this link on another thread, posted by Sef:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

