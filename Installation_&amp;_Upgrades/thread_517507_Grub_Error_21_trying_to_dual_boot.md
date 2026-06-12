---
title: "Grub Error 21 trying to dual boot"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by THEembodyment on 2007-08-04
I have two serial ATA 80GB drives that I originally configured in RAID0.  Then I installed XP Pro on the first 60GB and an extra 15GB NTFS partition.  Later, I decided to install Ubuntu 7.04 as well.  When I went through the installation, I selected to use the entire sdb partition.  After the error 21 message, I tried to load the XP startup disk to recover the MBR, but it would not load.  Anyway, from the Ubuntu live CD, I ran fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7833    62918541    7  HPFS/NTFS
/dev/sda2            7834        9138    10482412+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9541    76638051   83  Linux
/dev/sdb2            9542        9729     1510110    5  Extended
/dev/sdb5            9542        9729     1510078+  82  Linux swap / Solaris

Also, here is my menu.lst:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5ea6fecf-55ee-4421-a1dc-05e7ca2d1f0b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5ea6fecf-55ee-4421-a1dc-05e7ca2d1f0b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

So, I'm not exactly sure what to do now.  Thanks in advance for your help.

---

### Post by Pumalite on 2007-08-04
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

[http://ubuntuforums.org/showthread.php?t=514523](http://ubuntuforums.org/showthread.php?t=514523)

---

