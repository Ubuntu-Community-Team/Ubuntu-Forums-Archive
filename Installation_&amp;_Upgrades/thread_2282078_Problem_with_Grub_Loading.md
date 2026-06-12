---
title: "Problem with Grub Loading"
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by Miral_Hassni on 2015-06-11
First I have installed Windows 7 and than install Ubuntu after installing Ubuntu restart my computer now directly windows os starting please what i can do to enable Ubuntu Grub loader for starting Ubuntu.
PLEASE BE QUICK FOR RESPONSE

---

### Post by oldfred on 2015-06-11
Best to see details, so we know what to suggest.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Bashing-om on 2015-06-11
Miral_Hassni; Hi ! Welcome to the forum.

An easy thing to install grub . But it must be installed to the proper place. We need to find that where.
Please boot up the liveDVD(USB) in "try ubuntu" mode to a terminal (at the desktop key combo ctl+alt+t yields a terminal ).
Post back the output of terminal command:
```

sudo fdisk -lu

```
which will detail the hard drive(s) partitioning, such that we know what we are working with.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]ain't nothing but a thing
[/INDENT]

---

### Post by Miral_Hassni on 2015-06-12
this is the showing code what i can do to enable grub for use ubuntu
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e2ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   264544255   131912704    7  HPFS/NTFS/exFAT
/dev/sda3       264544256   528369663   131912704    7  HPFS/NTFS/exFAT
/dev/sda4       651251710   976771071   162759681    f  W95 Ext'd (LBA)
/dev/sda5       651251712   832899071    90823680    7  HPFS/NTFS/exFAT
/dev/sda6       832901120   955779071    61438976    7  HPFS/NTFS/exFAT
/dev/sda7       955781120   976771071    10494976   83  Linux

Disk /dev/sdb: 8179 MB, 8179941376 bytes
248 heads, 63 sectors/track, 1022 cylinders, total 15976448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8a23c6ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15952103     7976020+   b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by yancek on 2015-06-12
The output in your last post does show a Linux partition (sda7) but it would probably be best if you could post the output of the bootrepair BootInfo Summary suggested above.  This will give more detailed information such as whether you are using MBR or UEFI.  The bootloader for Ubuntu hasn't been properly installed and this information will be useful for someone to make a suggestion.

---

### Post by Miral_Hassni on 2015-06-16
Problem Resolved

---

