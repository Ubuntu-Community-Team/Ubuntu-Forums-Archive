---
title: "Cannot mount second harddisk - wrong fs type"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by volmark on 2008-06-26
I have installed second SATA HD drive (the boot one is SCSI) but couldn&#8217;t mount it properly. I&#8217;ve formatted it with fsck.ext3 and partitioned with TestDisk (external CD).
The system reports following error:
"mount: wrong fs type, bad option, bad superblock on /dev/sdb1"
Here are some listings of /etc/fstab and screen dumps of fdisk.
NOTE: It is server. No GUI utilities such "gparted" are possible

~$ sudo fdisk -l

Disk /dev/sda: 36.4 GB, 36419584000 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3cd54c8

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4240 34057768+ 83 Linux
/dev/sda2 4241 4427 1502077+ 5 Extended
/dev/sda5 4241 4427 1502046 82 Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3b64465

Device Boot Start End Blocks Id System
/dev/sdb1 1 9729 78148161 83 Linux

--------------------------------------------------------------------

~$ sudo nano /etc/fstab
GNU nano 2.0.7

File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=1010ffdb-c0fb-4f1d-9e65-589160c3bcd8 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=dd32c617-6437-42ce-b3dc-17a9977fa74c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

# 2. HD
/dev/sdb1 /media/hd2 ext3 defaults 0 0
--------------------------------------------------------------------
~$ sudo mount -a
--------------------------------------------------------------------
~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

---

### Post by volmark on 2008-06-26
Is it a wrong forum? There is no reaction to the issue. What shell I do so??? Is it possible to move the thread to other, more relevant forums?

---

### Post by VMC on 2008-06-26
Why did you use "fsck.ext3", and not "gparted" to format the drive?
In fact I didn't know you could format using that tool.

Edit: okay I see, you used testdisk. I've heard that tool used for repaits. I still use gparted to format and/or partition my hard drive. Of even cfdisk.

---

### Post by volmark on 2008-06-27
Little bit confused … In all manuals “fsck.ext3” presented as HD formatting and partitioning tool

---

### Post by volmark on 2008-06-27
Unfortunately I cannot use "gparted" because I don’t have GUI. I can use only command line utilities.

---

### Post by volmark on 2008-06-27
I have found some rapports about “cfdisk” errors:

cfdisk creates invalid (!) partion tables on disk
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/198248](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/198248)

Id say the disk was ****** - it cant get the disk size and therefore I cant format
[http://ubuntuforums.org/showthread.php?t=34819](http://ubuntuforums.org/showthread.php?t=34819)

I don’t want to occasionally loose my primary disk that’s why I need reliable methods.

---

### Post by kelvin spratt on 2008-06-27
Download a live version of Gparted/ Pmagic 2.0 or later and boot into the live disc then your drives are not mounted to your system. Try disc check first as this does not destroy any data and hopefully the disc will mount on reboot. note all partitioning should be done in isolation of the distro.

---

### Post by volmark on 2008-06-27
The host machine is placed in basement and it is a pure Linux box without display and keyboard. It can only be managed through remote terminal.
If I’m going to use Live CD I need to carry the computer up to 3. floor because there is no system consol in basement.
Are there other possibilities to do it remotely through terminal emulator like Putty??

---

### Post by volmark on 2008-06-27
Reformatted with fdisk in accordance with [http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.CLIPartitioning](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.CLIPartitioning)
Still impossible to mount second hard drive

:~$ sudo mount /dev/sdb1 /media/hd2/
mount: you must specify the filesystem type

~$ sudo mount -t ext3 /dev/sdb1 /media/hd2/
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog &#8211; try dmesg | tail  or so

~$ sudo fdisk -l

Disk /dev/sda: 36.4 GB, 36419584000 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3cd54c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4240    34057768+  83  Linux
/dev/sda2            4241        4427     1502077+   5  Extended
/dev/sda5            4241        4427     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3b64465

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

What's wrong ???

---

