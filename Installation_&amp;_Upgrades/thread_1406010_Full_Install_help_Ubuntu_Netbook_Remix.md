---
title: "Full Install help Ubuntu Netbook Remix"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by ccondardo on 2010-02-13
Hey guys,

New ubuntu user here. I made an ISO for UNR and installed it and it worked fine. But when I unplug the external CD drive I used to install the ISO the mini boots to windows again. I assume I'm not doing the install correctly but I've tried to do all of the choices on the initial menu to no avail. Any ideas? I am on a Dell Mini 9.

Thanks!

~Corey

---

### Post by darkod on 2010-02-13
Boot with the ubuntu cd again, but select the Try Ubuntu option to load the live desktop. In terminal run:

sudo fdisk -l

to confirm you have linux partitions on the hdd. You can also post the results here. After that we'll see.

---

### Post by ccondardo on 2010-02-13
I typed this into the terminal: (just so you know I'm a noob with the terminal)

sudo fdisk

I then pressed enter and this returned:

Unable to open - 

Usage: fdisk [-l] [-b SSZ] [-u] devilce
E.g.: fdisk /dev/hda (for the first IDE disk)
  or: fdisk /dev/sdc (for the third SCSI disk)
  or: fdisk /dev/eda (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0 or: fdisk /dev/ida/c0d0 (for RAID devices)

Thoughts?

~Corey

---

### Post by ccondardo on 2010-02-14
I'm still having trouble with this, any ideas?

~Corey

---

### Post by darkod on 2010-02-14
You needed to put -l (small L), exactly as I wrote it.

sudo fdisk -l

Copy the result here.

---

### Post by bowbalitic on 2010-02-14
You need the lowercase L after fdisk
like

sudo fdisk -l

copy and paste this if you have to

the L tells fdisk to "list" the partitions on your drive

Here is an example of mine to show you

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bcffc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19581   157284351   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00052f46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13054   104856223+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00058409

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          36      289138+  83  Linux
/dev/sdc2           18831       19452     4996215   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```You should only have one device /dev/sda

EDIT 

Looks like Darkod beat me :P

---

### Post by ccondardo on 2010-02-14
Thanks for the help guys. I couldn't figure out that was an L,lol.

Here are the results.

```
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 7682 MB, 7682605056 bytes
255 heads, 63 sectors/track, 934 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7         934     7451648    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

```

Is that better?

~Corey

---

### Post by darkod on 2010-02-14
Depending what you call better. :)
Yes, it does show us more, but you don't have a Linux partition there. Compare with the results posted by the previous poster. You can clearly see the Linux partition.

So, you either installed (or tried to install) wubi inside windows, or somehow your ubuntu install didn't even start.

Also, it seems you only have 8GB SSD. That is rather small, do you plan to have only UNR? In that case the /dev/sda2 partition shouldn't be ntfs at all.

If you plan to have only UNR, boot again with the stick, select Try Ubuntu first to see how it will run on your netbook. If you are happy, click the Install icon on the desktop (or reboot again and select Install Ubuntu from the menu) and in step 4 when it asks where to install, select the Erase and use whole disk option. That will ERASE everything on your hdd, so first copy everything you need from it.
That option will create a default UNR setup on your 8GB SSD.

---

### Post by ccondardo on 2010-02-14
Thanks Darko,

Yes I'm using a Dell Mini and all I want is UNR. I will try those steps and let you know how it goes. Thanks again for the help!

~Corey

---

