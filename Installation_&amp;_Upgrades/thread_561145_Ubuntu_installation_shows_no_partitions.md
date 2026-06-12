---
title: "Ubuntu installation shows no partitions"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by zodox on 2007-09-27
I'm trying to install Ubuntu, but it does not show my partitions just a big empty disk of unallocated space. And therefore I can't select any root filesystem or swap. In fact I have 6 partitions, they show up fine in fdisk though. And I don't wont to alter the partition table in any way (already have 2 linux partitions). I have tested bouth the regular live cd and the alternative non graphical cd. 

Any ideas?

---

### Post by Pumalite on 2007-09-27
Post:
sudo fdisk -lu (from Live CD if you have to)

---

### Post by zodox on 2007-09-27
fdisk shows all the partitions (fdisk -l). The rescue mode on the cd also show all 6 partitions.

---

### Post by Pumalite on 2007-09-27
Copy and paste here either from a Linux OS or Ubuntu Live CD. The entire output please, so we can help you.

---

### Post by zodox on 2007-09-27
ubuntu@ubuntu:~$ sudo fdisk -lu

[HTML]Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20482874    10241406    7  HPFS/NTFS
/dev/sda2        20482875   268414019   123965572+   f  W95 Ext'd (LBA)
/dev/sda3        81915498   268414019    93249261    7  HPFS/NTFS
/dev/sda4       268414020   586099394   158842687+   7  HPFS/NTFS
/dev/sda5        20483001    22587389     1052194+  82  Linux swap / Solaris
/dev/sda6   *    22587453    81915434    29663991   83  Linux[/HTML]

---

### Post by Pumalite on 2007-09-27
You have a Linux in sda6. Is that the Ubuntu you installed or another Linux?

---

### Post by zodox on 2007-09-27
It's an old copy of Ubuntu.

Here's a screenshot from the installation:

---

### Post by Pumalite on 2007-09-27
Works fine it seems. And is recognized by the system and BIOS if you are posting from there. Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
(stand alone, burn to CD, boot from, program) and see if it recognizes your partitions. If it does, prepare sda6 with 10 GB for '/' and the rest for /home all formated ext3. And install with Alternate CD using your already awaiting partitions.

---

### Post by zodox on 2007-09-27
gparted gives the exact same result as the installation.

---

### Post by Pumalite on 2007-09-27
Use rescuecd: [http://www.sysresccd.org/Download.en.php](http://www.sysresccd.org/Download.en.php) and it's partitioner then.

---

### Post by zodox on 2007-09-27
Would that make a difference? I don't realy want to change the partition table. I just want the Ubuntu installation to find my sda6 partition so I can install it.

Is it possible to install ubuntu from command line?

---

### Post by Pumalite on 2007-09-27
You have to fix the problem of your partition not being recognized by the installer.

---

