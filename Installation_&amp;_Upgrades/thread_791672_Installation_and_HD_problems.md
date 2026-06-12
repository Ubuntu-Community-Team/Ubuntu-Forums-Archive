---
title: "Installation and HD problems"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by jimmybond on 2008-05-12
First of all, much apologies for a long post, repeated topics in the forum, as I am very much a beginner.

I'm currently running a dual boot desktop with Ubuntu (7.10) and Windows XP Professional on two separate physical hard drives connected in PATA.  Several problems:

1. Apparently, I have some hard drive clicking problems (two consecutive clicks every 2-5 seconds when I boot or try to install something) and I've searched around and it seems to be a hard drive "parking" problem that involves APM and can be disabled by using the code 
```
sudo hdparm -B 255 /dev/sdb
```.  
I've tried that using both 255 and 254 in the terminal and I get ```
setting Advanced Power Management level to disabled
HDIO_DRIVE_CMD failed: Input/output error
```.  Then I wondered if the drive names are correct and did 
```
sudo fdisk -l
```, which yields:
```
jimmy@ubuntu-desktop:~$ sudo fdisk -l


Disk /dev/sda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29af29ae

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1246    10008463+   7  HPFS/NTFS


Disk /dev/sdb: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47d047cf

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         494     3968023+  83  Linux
/dev/sdb2             495         524      240975    5  Extended
/dev/sdb5             495         524      240943+  82  Linux swap / Solaris 
```
Maybe it's some other problem.

2. I've also read that some of these issues can be resolved by upgrading.  Should I upgrade to 8.04?  It seems that the wireless network (Intel 2915ABG) is working, but I have no idea how to upgrade the default drivers for the device.  As for upgrading Ubuntu, I can try using the System > Administration > Update Manager but that does not open and gives me the same clicking noises as described before.  

3. This was a previous problem that doesn't really seem to have a solution, but the configuration I have now is annoying, but doable.  I need to enable and disable the individual hard drives in Dell's BIOS each time I want to boot into Ubuntu, as there are no options to dual boot. The grub menu only appears after I disable the Windows XP drive in BIOS, (so obviously when I select Windows XP from grub, it will not boot).  I think this a BIOS problem and I think it is the most recent version, so I don't mind if there's no solution.

If you took all the time to read all of this, thanks!  Any ideas/suggestions/solutions will be greatly appreciated! heh.

---

