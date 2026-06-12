---
title: "Grub Problems - Error 21"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by markekeller on 2008-07-15
I just upgraded Linux Mint (a distro based on Ubuntu Hardy) to the newest version (using a Live CD), and when I rebooted, I found I couldn't get into my system.  No matter what I selected from the GRUB menu - regular boot, recovery mode, memtest or Windows XP - I get the following error:

```
Error 21: selected disk does not exist.
```

I tried installing it again, and still the same problem.  What could be causing this?  I installed the last version of Linux Mint the same way, about six months ago, and GRUB worked fine.  I've got two hard drives, formatted the following way:
> /dev/sda SATA Drive
[INDENT]/dev/sda1 xfs # will be mounted as /home
/dev/sda2 xfs # will be mounted as /usr/local[/INDENT]
/dev/sdb IDE Drive
[INDENT]/dev/sdb1 ntfs
/dev/sdb2 ext3 # where I'm installing Linux Mint[/INDENT]
And a small swap partition on both drives.  The master boot record was installed on sdb2, I think (the last version of Linux Mint called it hdb2); and I've tried it both on there and on the other drive, since I reinstalled.  GRUB came up properly, though, so I don't think the location is what's causing the problem.

And just now I noticed that GParted shows a warning icon next to the ntfs partition, and when I view its information, there's a warning message:

> Failed to startup volume: Invalid argument.
Failed to mount '/dev/sdb1': Invalid argument.
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

ntfsresize v2.0.0 (libntfs 10:0:0)
Failed to startup volume: Invalid argument.
ERROR(22): Opening '/dev/sdb1' as NTFS failed: Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
if the disk was incorrectly repartitioned (see the ntfsresize FAQ).

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.

But the only partition I formatted was the ext3 one (I want to keep my data in /home and /usr/local, and, of course, in Windows).  And Windows worked fine when I used it on Saturday.

I'm in some real deep trouble here, it looks like.  Does anyone know what to do?  Please help, and thanks!

---

### Post by Sef on 2008-07-15
With the Live CD, Applications > Accessories > Terminal

then type or copy/paste in this code:

```
fdisk -l
``` Small L

It will show exactly how your partitions are partitioned.

Also check to make sure that your wires are not loose.

GRUB error 21:

> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

---

### Post by markekeller on 2008-07-15
Here's the output (with a rather appropriate fortune):

```
 ________________________________________
/ You may my glories and my state        \
| dispose, But not my griefs; still am I |
| king of those.                         |
|                                        |
\ -- William Shakespeare, "Richard II"   /
 ----------------------------------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

mint@mint ~ $ fdisk -l
mint@mint ~ $ fdisk -l
mint@mint ~ $ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4675    37551906   83  Linux
/dev/sda2            4676        9349    37543905   83  Linux
/dev/sda3            9350        9726     3028252+   5  Extended
/dev/sda5            9350        9726     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6530    52452193+   7  HPFS/NTFS
/dev/sdb2            6531        9816    26394795   83  Linux
/dev/sdb3            9817        9964     1188810    5  Extended
/dev/sdb5            9817        9964     1188778+  82  Linux swap / Solaris
mint@mint ~ $
```

It all looks okay . . . it's kind of late, so I'll check the wires in the morning.  I kind of doubt that anything's unplugged, though; because fdisk detected it all, I haven't bumped my box recently, and *all* the partitions give the same error - and the two disks connect to the motherboard with seperate cables.  It's weird indeed.  Any other ideas?

---

### Post by markekeller on 2008-07-15
Alright, I checked the BIOS, and everything seems to be detected.  Fdisk wouldn't detect my hardware, anyway, if the BIOS didn't; right?

What else could be wrong?

---

