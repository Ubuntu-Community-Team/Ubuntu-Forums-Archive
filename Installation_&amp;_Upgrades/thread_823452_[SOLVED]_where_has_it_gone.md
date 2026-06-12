---
title: "[SOLVED] where has it gone"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Jon Williams on 2008-06-09
Hi 

I finally did it, i bit the bullet, Ihave installed linux, it was easy, all went to plan!

Until

I got the message to reboot, I took the CD out

and up pops

error loading OS

HELP!!!!

I am already running windows XP and was hoping to dual boot, I know that i can at least get into ubuntu through the boot CD, but if anyone has any suggestions I am all ears!

Thanks
J

---

### Post by Vadi on 2008-06-09
Can you tell us what the error says?

---

### Post by Steveway on 2008-06-09
Providing the minimal information I assume that Grub hasn't been installed to the MBR or that it has been installed to the wrong disk.
The easiest way would be to get and burn the SuperGrub disk and then tell it to recover Grub. It should pick up everything and you should then again be able to boot.

---

### Post by Sef on 2008-06-09
Using the live cd, check your partitions;

Application > Accessories > Terminal

then type in this code:

```
sudo fdisk -l
``` small L, then paste the results here.

---

### Post by Jon Williams on 2008-06-09
Hi
All I get is a black screen, in the top left hand corner it says

Error loading operating system_

thats it?

All the ablove sounds good but if I am honest I havent got a clue

J

---

### Post by Jon Williams on 2008-06-09
ok I have tried the Sudo fdisk thingy and this is what I got, hope it helps


Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99ca99ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14948   120069778+   7  HPFS/NTFS
/dev/sda2   *       14949       24415    76043677+  83  Linux
/dev/sda3           24416       24792     3028252+   5  Extended
/dev/sda5           24416       24792     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdacfd466

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdacfd463

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdacfd464

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        9729    78148161    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by Jon Williams on 2008-06-11
does the above make any sense to any one?

Please help!

J

---

