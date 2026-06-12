---
title: "I broke my Swap file"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by Robster2 on 2009-12-29
Toshiba laptop AMD 64x2 4Gig Memory.  Ubuntu 64bit 9.04

/dev/sda6 Is my Ubuntu 
/dev/sda7 swap partition 

I have no idea what /dev/sda5,/dev/sda4/and /dev/sd3 are.

The size of /dev/sda4 is clearly wrong

found that I had free space on my computer so I increased my swap partition using Gparted from about 1 gig to about 6gigs.

Now on boot up I get whole lot of text like you do when you use the recovery boot up, which did not happen before.

Available Swap ........ fail (in red letters).

Tried

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

sudo swapoff -a
sudo /sbin/mkswap /dev/sda7
sudo swapon -a

It did not work.
Bellow are the out puts of 

rob@rob-laptop:~$ sudo fdisk -l
rob@rob-laptop:~$ sudo blkid
root@rob-laptop:~# cat /etc/fstab
root@rob-laptop:~# ls -l /dev/disk/by-uuid/

/-------------------------------------------------------------------------/
rob@rob-laptop:~$ sudo fdisk -l
[sudo] password for rob:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c22b44

Device Boot Start End Blocks Id System
/dev/sda1 1 192 1536000 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 192 21106 167996120+ 7 HPFS/NTFS
/dev/sda3 21107 21410 2441816 83 Linux
/dev/sda4 21411 30401 72220207+ f W95 Ext'd (LBA)
/dev/sda5 21411 21432 176672 82 Linux swap / Solaris
/dev/sda6 21433 29237 62693628 83 Linux
/dev/sda7 29238 30036 6417936 82 Linux swap / Solaris

/--------------------------------------------------------------------------/

rob@rob-laptop:~$ sudo blkid
[sudo] password for rob:
/dev/sda1: UUID="6412F89712F86F82" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs"
/dev/sda2: UUID="CC2C27F02C27D46C" LABEL="S3A6611D005" TYPE="ntfs"
/dev/sda3: UUID="3247aa89-17cf-40f0-8716-2cb7b1546354" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="1b3806e1-952a-4d5f-a7b0-40efc14bd0dc"
/dev/sda6: UUID="9bf4bbd1-dff9-4462-9cf0-6eab2df92d1f" TYPE="ext3"
/dev/sda7: TYPE="swap" UUID="5de1df7f-15f2-41ce-bf79-c1d6a235a473"
rob@rob-laptop:~$

/--------------------------------------------------------------------------/
root@rob-laptop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda5 during installation
UUID=9bf4bbd1-dff9-4462-9cf0-6eab2df92d1f / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=d0fb723e-86a4-4b09-9064-6ca388a7ef18 none swap sw 0 0
# swap was on /dev/sda8 during installation
UUID=1b3806e1-952a-4d5f-a7b0-40efc14bd0dc none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
root@rob-laptop:~#

/------------------------------------------------------------------------/
root@rob-laptop:~# ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 1b3806e1-952a-4d5f-a7b0-40efc14bd0dc -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 3247aa89-17cf-40f0-8716-2cb7b1546354 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 5de1df7f-15f2-41ce-bf79-c1d6a235a473 -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 6412F89712F86F82 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 9bf4bbd1-dff9-4462-9cf0-6eab2df92d1f -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 CC2C27F02C27D46C -> ../../sda2
root@rob-laptop:~#

Thank you for your help

---

### Post by taurus on 2009-12-29
> **Robster2 said:**
> Toshiba laptop AMD 64x2 4Gig Memory.  Ubuntu 64bit 9.04

/dev/sda6 Is my Ubuntu 
/dev/sda7 swap partition 

I have no idea what /dev/sda5,/dev/sda4/and /dev/sd3 are.

The size of /dev/sda4 is clearly wrong

found that I had free space on my computer so I increased my swap partition using Gparted from about 1 gig to about 6gigs.

Now on boot up I get whole lot of text like you do when you use the recovery boot up, which did not happen before.

Available Swap ........ fail (in red letters).

Tried

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

sudo swapoff -a
sudo /sbin/mkswap /dev/sda7
sudo swapon -a

It did not work.
Bellow are the out puts of 

rob@rob-laptop:~$ sudo fdisk -l
rob@rob-laptop:~$ sudo blkid
root@rob-laptop:~# cat /etc/fstab
root@rob-laptop:~# ls -l /dev/disk/by-uuid/

/-------------------------------------------------------------------------/
rob@rob-laptop:~$ sudo fdisk -l
[sudo] password for rob:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c22b44

Device Boot Start End Blocks Id System
/dev/sda1 1 192 1536000 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 192 21106 167996120+ 7 HPFS/NTFS
/dev/sda3 21107 21410 2441816 83 Linux
/dev/sda4 21411 30401 72220207+ f W95 Ext'd (LBA)
/dev/sda5 21411 21432 176672 82 Linux swap / Solaris
/dev/sda6 21433 29237 62693628 83 Linux
/dev/sda7 29238 30036 6417936 82 Linux swap / Solaris

/--------------------------------------------------------------------------/

rob@rob-laptop:~$ sudo blkid
[sudo] password for rob:
/dev/sda1: UUID="6412F89712F86F82" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs"
/dev/sda2: UUID="CC2C27F02C27D46C" LABEL="S3A6611D005" TYPE="ntfs"
/dev/sda3: UUID="3247aa89-17cf-40f0-8716-2cb7b1546354" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="1b3806e1-952a-4d5f-a7b0-40efc14bd0dc"
/dev/sda6: UUID="9bf4bbd1-dff9-4462-9cf0-6eab2df92d1f" TYPE="ext3"
/dev/sda7: TYPE="swap" UUID="**[COLOR="Blue"]5de1df7f-15f2-41ce-bf79-c1d6a235a473[/COLOR]**"
rob@rob-laptop:~$

/--------------------------------------------------------------------------/
root@rob-laptop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda5 during installation
UUID=9bf4bbd1-dff9-4462-9cf0-6eab2df92d1f / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=**[COLOR="Red"]d0fb723e-86a4-4b09-9064-6ca388a7ef18[/COLOR]** none swap sw 0 0
# swap was on /dev/sda8 during installation
UUID=1b3806e1-952a-4d5f-a7b0-40efc14bd0dc none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
root@rob-laptop:~#

/------------------------------------------------------------------------/
root@rob-laptop:~# ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 1b3806e1-952a-4d5f-a7b0-40efc14bd0dc -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 3247aa89-17cf-40f0-8716-2cb7b1546354 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 5de1df7f-15f2-41ce-bf79-c1d6a235a473 -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 6412F89712F86F82 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 9bf4bbd1-dff9-4462-9cf0-6eab2df92d1f -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-12-30 06:34 CC2C27F02C27D46C -> ../../sda2
root@rob-laptop:~#

Thank you for your help

An entry for one of the swap partitions is wrong in /etc/fstab (first entry).  You need to change the UUID to the new one (for /dev/sda7).

---

### Post by tripolitan on 2009-12-30
Everything looks normal, sda4 is an extended partition (extended=logical and not to be confused with the Second Extended file system, they are different things) the size of /dev/sda4 is exactly what it should be (the sum of all partitions that were created within it)

There are several ways to fix this, the easiest is to edit fstab and reboot.
For swap to work, your fstab should look like this (comment out the uuid stuff):

proc /proc proc defaults 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 / ext3 relatime,errors=remount-ro 0 1
/dev/sda7 none swap sw  0       0 

otherwise, major file system surgery is needed to rectify this mess. If this is a new, un-upgraded install, I would suggest re-installing but taking extra care in partitioning. (with 4GB RAM, you do not need all that swap)

---

### Post by Robster2 on 2009-12-30
> **taurus said:**
> An entry for one of the swap partitions is wrong in /etc/fstab (first entry).  You need to change the UUID to the new one (for /dev/sda7).

Well I replaced it, rebooted, but it did not make any difference. Did I do something wrong? Thanks anyway.


root@rob-laptop:/etc# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9bf4bbd1-dff9-4462-9cf0-6eab2df92d1f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5de1df7f-15f2-41ce-bf79-c1d6a235a473 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=1b3806e1-952a-4d5f-a7b0-40efc14bd0dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Robster2 on 2009-12-30
> **tripolitan said:**
> Everything looks normal, sda4 is an extended partition (extended=logical and not to be confused with the Second Extended file system, they are different things) the size of /dev/sda4 is exactly what it should be (the sum of all partitions that were created within it)

There are several ways to fix this, the easiest is to edit fstab and reboot.
For swap to work, your fstab should look like this (comment out the uuid stuff):

proc /proc proc defaults 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 / ext3 relatime,errors=remount-ro 0 1
/dev/sda7 none swap sw  0       0 

otherwise, major file system surgery is needed to rectify this mess. If this is a new, un-upgraded install, I would suggest re-installing but taking extra care in partitioning. (with 4GB RAM, you do not need all that swap)

:lolflag:  We have a winner :lolflag:

Problem is solved

Out of interest where did I go wrong???

---

