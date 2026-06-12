---
title: "Installed Windows Over Ubuntu"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by abshirf2 on 2008-05-24
Hello all

Last month i installed windows on my machine (nothing else) - then i installed ubuntu alongside it (partitioned). For some reason i installed another windows OS on my machine. Of course the **GRUB loader is gone**.

How can i get it back without having to install ubuntu again?

Just to add - I have a gusty gibbon CD now, the other CD i installed with was 6.0 version, I don't have this anymore.

Sorry for the wooly question, any clarifications needed please let me know :)

Thank you all

---

### Post by cdtech on 2008-05-24
You can do this by booting into the live Ubuntu cd.

While in Ubuntu bring up a terminal and type:
sudo fdisk -l

This will list the devices you have installed.

example fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f29dfaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18359   147468636    7  HPFS/NTFS
/dev/sda2           18360       19457     8819685    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000116f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         638     5124703+  83  Linux
/dev/sdb2             639        8750    65159640    5  Extended
/dev/sdb3            8751       30401   173911657+   7  HPFS/NTFS
/dev/sdb5             639        1307     5373711   82  Linux swap / Solaris
/dev/sdb6            1308        6413    41013913+  83  Linux
/dev/sdb7            6414        8750    18771921   83  Linux
```

You can see the MBR on each disk with the asterik under boot.

To install the GRUB bootloader into the primary drive, in a terminal:
sudo grub

This will put you into a grub shell >
type:
setup (hd0)
### this will be for the first drive (sda)
### (hd1) would be for sdb, ect,,,,,

Then type quit to exit the grub shell.

You have now installed the GRUB bootloader code into the MBR for that device.

Hope this helps......

---

### Post by animefan82 on 2008-05-24
Do you have access to ubuntu? If not, it can still be done with an installation cd.
First you need to execute a shell, then type

sudo grub

which will take you to the grub shell. Here you type

find /boot/grub/stage1

which will return 

(hdx,y) , where x is the drive and y is the partition number

now that you know this, type

root (hdx,y) , where (hdx,y) is what you found out using find

and finally

setup (hdx) , which will install grub on the drive's master boot record (mbr)

--EDIT START--
type
quit , to exit grub
--EDIT END--
This should make grub also install a loader for any other os currently on your system. If this doesn't happen we can take it from there. Let us know if it worked.

---

### Post by abshirf2 on 2008-05-24
Thank you for your replies guys :) - I am starting my machine to try it.

I have access to ubuntu via windows using a small program that lets me look at files in partitions. Is there an easier way, i mean using a GUI! xD

---

### Post by animefan82 on 2008-05-24
There are GUIs around, I guess, but this IS in fact, much easier than any GUI around.

---

### Post by abshirf2 on 2008-05-24
Understood, I am going to attempt it now.

---

### Post by abshirf2 on 2008-06-21
After I finally got round to this, the grub loader works, but I have a bigger problem!!!

If try to access any of my ubuntu OS's i get this error:
```

root (hd0,1)

Filesystem Type Unknown, partition type 0xf
Kernel /boot/vmlinuz.....
b3b ro quiet splash

Error 17: Cannot mount selected Partition
```

Please help!!!

I hate it when a problem is solved and it leads to another!

---

### Post by abshirf2 on 2008-06-28
Help!!

---

