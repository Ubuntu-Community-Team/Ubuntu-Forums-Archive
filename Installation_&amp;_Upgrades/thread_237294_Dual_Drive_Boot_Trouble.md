---
title: "Dual Drive Boot Trouble"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by Trae on 2006-08-15
So a bit about my system. I am using 3x250g hardrives. 2 are SATA and 1 is EIDE. The first SATA has a fresh Windows install on it. I went and installed Ubuntu on the second SATA drive. Afterwards I reset and my computer came up into Windows. I expected this since I don't remember configuring any boot selecting programs. So I reset again and this time loaded up my motherboards boot selector and selected the drive Ubuntu is on. My computer said "Verifying Data..." and didn't do anything. The harddrive isn't even being accessed. Any idea what's gone wrong?

---

### Post by confused57 on 2006-08-15
Boot up with the Desktop Live CD and open a terminal(Applications---Accessories---Terminal) and enter:
```
sudo fdisk -l
```
The -l is a small "L".

This will show your partition tables and how Ubuntu recognizes your drives.  Sometimes when there is a mix of SATA and IDE drives and Ubuntu is installed on a SATA drive, for some reason Ubuntu installs grub to the IDE drive?

Grub can be installed manually with the Live CD also:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Post the output of the above command, may help someone come up for a solution for you.

---

### Post by Trae on 2006-08-16
This is what I got.

> Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           5       30515   245079576    7  HPFS/NTFS
/dev/sda2               2           4       24097+   5  Extended
/dev/sda5               2           4       24066    4  FAT16 <32M

Partition table entries are not in disk order

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30138   242083453+  83  Linux
/dev/sdb2           30139       30515     3028252+   5  Extended
/dev/sdb5           30139       30515     3028221   82  Linux swap / Solaris

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       30401   244196001    7  HPFS/NTFS


---

### Post by Xceptiona1 on 2006-08-16
I have a similar issue, I might be able to try to same fix...of installing GRUB manually.

I have an IDE drive and a SATA drive. The Sata is where I installed XP Home, and I also put ubuntu dapper after that. My problem is when I reboot after the Ubuntu install it doesnt even look/ go to GRUB it just boots strait to windows. 

Do you think that GRUB is just installing to the IDE drive? Would I just follow the same link to fix my issue as well? Thank you

---

### Post by Trae on 2006-08-16
Yep, the problem was Grub was installing on the IDE drive. When I tried booting from there I got an "error 17". I followed the instructions in the manual install but instead told it to install on (hd,1). Hope this helps.

---

### Post by Xceptiona1 on 2006-08-16
Is this somthing that is a documented bug within GRUB, or should we submit a bug report. Im guessing we arent the first folks to have this issue. I think it's probably a very common issue, with folks having SATA and IDE.

---

