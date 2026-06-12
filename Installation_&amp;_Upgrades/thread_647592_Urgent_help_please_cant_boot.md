---
title: "Urgent help please cant boot"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by thebloggu on 2007-12-22
i had ubuntu installed and wanted to uninstall so i deleted the partitions. but now i try to boot and grub gives an error (17 but had 22 already) and im not able to run windows. i tried to recover (i have a recovery partition but not recovery cd) but it still returns error. dont know what to. im writing this in live cd

i have an asus f3jc and windows xp

please help its urgent

---

### Post by Pumalite on 2007-12-22
Boot your XP CD>Recovery>FIXMBR>FIXBOOT.

---

### Post by meierfra on 2007-12-22
Click on FixMBR in my signature. It gives two ways to  fix the mbr without  a windows recovery CD.  Try the last method first.

---

### Post by thebloggu on 2007-12-22
ok did what you said but it returns this on the third step of the last option

```
ubuntu@ubuntu:~$ sudo ms-sys -m /dev/sda2
/dev/sda2 seems to be a disk partition device,
use the switch -f to force writing of a master boot record
ubuntu@ubuntu:~$ sudo ms-sys -f /dev/sda2
/dev/sda2 has a FAT32 file system.
/dev/sda2 has an x86 boot sector,
it is an unknown boot record
ubuntu@ubuntu:~$ sudo ms-sys -m /dev/sda2
/dev/sda2 seems to be a disk partition device,
use the switch -f to force writing of a master boot record
ubuntu@ubuntu:~$ sudo ms-sys -m /media/disk
Unable to open /media/disk, Is a directory
ubuntu@ubuntu:~$ sudo ms-sys -m /dev/sda2
/dev/sda2 seems to be a disk partition device,
use the switch -f to force writing of a master boot record
ubuntu@ubuntu:~$ sudo ms-sys -m /dev/sda2
```

what should i do?

@pumalite i dont have xp cd

---

### Post by meierfra on 2007-12-22
If you  have  a second computer to burn a cd, try supergrub (see my signature). 

Otherwise post the output of

```
sudo fdisk -l
```

---

### Post by Pumalite on 2007-12-22
Use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Read the instructions and fix your Windows MBR.

---

### Post by meierfra on 2007-12-22
Actually this should work

> sudo ms-sys -m /dev/sda

---

### Post by thebloggu on 2007-12-22
this is the output

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         510     4096543+  1b  Hidden W95 FAT32
/dev/sda2   *         511        7501    56155207+   c  W95 FAT32 (LBA)
/dev/sda3            7502       12161    37431450    f  W95 Ext'd (LBA)
/dev/sda5            7502       12161    37431418+   b  W95 FAT32

```

should i use supergrub? right now i dont have cds to burn and no floppy :(

---

### Post by meierfra on 2007-12-22
Try my last suggestion (post 7). Should only take a second. If that does not work, supergrub will be your best option.

---

### Post by thebloggu on 2007-12-22
```
Windows 2000/XP/2003 master boot record successfully written to /dev/sda

```

guess it worked

thanks a lot to both for the answer :) ;)

i will reboot now

---

### Post by Pumalite on 2007-12-22
Get a CD with a friend and burn Super Grub. Super Grub is great and you are going to be needing it in the years ahead anyway.

---

### Post by meierfra on 2007-12-22
> Get a CD with a friend and burn Super Grub. Super Grub is great and you are going to be needing it in the years ahead anyway.

agree

---

### Post by Pumalite on 2007-12-22
You are welcome. Good luck!

---

