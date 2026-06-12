---
title: "partition recovery"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by dbnavan on 2010-03-12
Hi folks I am kinda new to linux have dabbled with it in the past but a very expierenced in Windows, would classify myself as a windows technician.


I installed ubuntu onto what i thought to be a secondary hard disk earlier but seem to have screwed up my system and now cant get to my windows partitian even though i still can see the files from the Live cd,

When I boot my machine I get a 'grub' rescue prompt.

If i boot from my live CD i can get the following info

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1551a083

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2040    16384000   27  Unknown
/dev/sda2   *        2040        2053      102400    7  HPFS/NTFS
/dev/sda3            2053       20483   148040704    7  HPFS/NTFS
/dev/sda4           20483       38914   148042072    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

can someone please tell me I can get my windows partition back, and how?

---

### Post by coffeecat on 2010-03-12
I presume you took out your secondary drive before you booted up the live CD, because otherwise it would have shown up as sdb.

Anyway, the reason you can't boot into Windows is that grub stage 1 has overwritten the MBR. Trouble is, grub stage 2 + the grub configuration menu are on the Ubuntu root partition (on sdb) so stage 1 has nowhere to go. Except that...

> **dbnavan said:**
> When I boot my machine I get a 'grub' rescue prompt.

Do you mean a grub error? In this situation you would normally get an error, not a rescue prompt. *

If you want to repair the MBR you can boot up with a Windows install disc (Microsoft - not an OEM disc image) and run FIXMBR from the repair console. Or, for two alternative methods of repairing the MBR, have a look at this thread, posts 2 and 3:

[http://ubuntuforums.org/showthread.php?t=1428167](http://ubuntuforums.org/showthread.php?t=1428167)

* **Edit:** sorry - was thinking of legacy grub where you get a grub error number. With grub2, you get:

> grub error 
*error message*
grub rescue<

or something like that. Anyway, the advice is the same. Repair the MBR because your NTFS partitions are still there according to that fdisk output.

---

