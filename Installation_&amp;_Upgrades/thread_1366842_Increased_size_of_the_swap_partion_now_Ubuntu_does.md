---
title: "Increased size of the swap partion now Ubuntu does not find it"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by Robster2 on 2009-12-28
I am using 9.04 64bit 4gigs of ram I found that I had free space on my computer so I increased my swap partition using Gparted from about 1 gig to about 5gigs.

Now on boot up I get whole lot of text like you do when you use the recovery boot up, which did not happen before.

One line

Available Swap   ........ fail (in red letters)

I did not rename the partition so I do not know how this happened.  

Help please?

---

### Post by x33a on 2009-12-28
if it was being mounted through uuid in /etc/fstab, then after resizing the uuid must have changed and that is causing the problem.

post the output of
```
cat /etc/fstab
ls -l /dev/disk/by-uuid/
```

---

### Post by Robster2 on 2009-12-28
rob@rob-laptop:~$ sudo -i
[sudo] password for rob: 
root@rob-laptop:~# cat /etc/fstab
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
UUID=d0fb723e-86a4-4b09-9064-6ca388a7ef18 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=1b3806e1-952a-4d5f-a7b0-40efc14bd0dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
root@rob-laptop:~# ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-12-30 01:19 1b3806e1-952a-4d5f-a7b0-40efc14bd0dc -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-12-30 01:19 3247aa89-17cf-40f0-8716-2cb7b1546354 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-12-30 01:19 4726e433-aba0-4330-a192-4bb8720db2b3 -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-12-30 01:19 6412F89712F86F82 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-12-30 01:19 9bf4bbd1-dff9-4462-9cf0-6eab2df92d1f -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-12-30 01:19 CC2C27F02C27D46C -> ../../sda2
root@rob-laptop:~#

/dev/sda6 ext3 is my Ubuntu partition
/dev/sda7 linux-swap should be my swap partition

Thanks

---

### Post by x33a on 2009-12-29
the uuid of sda5 is matching the uuid of swap (in fstab).

need to be more clear before making any changes.

could you please post the output of 
```
sudo fdisk -l
sudo blkid
```

---

### Post by Robster2 on 2009-12-29
I am afraid that I kept trying to fix the problem

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

sudo swapoff -a
sudo /sbin/mkswap /dev/sda7
sudo swapon -a

It did not work.

rob@rob-laptop:~$ sudo fdisk -l
[sudo] password for rob: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c22b44

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       21106   167996120+   7  HPFS/NTFS
/dev/sda3           21107       21410     2441816   83  Linux
/dev/sda4           21411       30401    72220207+   f  W95 Ext'd (LBA)
/dev/sda5           21411       21432      176672   82  Linux swap / Solaris
/dev/sda6           21433       29237    62693628   83  Linux
/dev/sda7           29238       30036     6417936   82  Linux swap / Solaris

rob@rob-laptop:~$ sudo blkid
[sudo] password for rob: 
/dev/sda1: UUID="6412F89712F86F82" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="CC2C27F02C27D46C" LABEL="S3A6611D005" TYPE="ntfs" 
/dev/sda3: UUID="3247aa89-17cf-40f0-8716-2cb7b1546354" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="1b3806e1-952a-4d5f-a7b0-40efc14bd0dc" 
/dev/sda6: UUID="9bf4bbd1-dff9-4462-9cf0-6eab2df92d1f" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="5de1df7f-15f2-41ce-bf79-c1d6a235a473" 
rob@rob-laptop:~$ 

For good measure I have repeated the original commands you gave in case I changed something.

root@rob-laptop:~# cat /etc/fstab
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
UUID=d0fb723e-86a4-4b09-9064-6ca388a7ef18 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=1b3806e1-952a-4d5f-a7b0-40efc14bd0dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
root@rob-laptop:~#

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

### Post by x33a on 2009-12-29
the cause of the problem is, that you have 2 swap partitions: sda5 & sda7. delete sda7 using gparted and then try mounting the swap. post the results here.

---

### Post by Robster2 on 2009-12-30
Sorry I did not think you were comming back to to me. So I reformated everything and posted again with a screen shot of Gparted and I got an answer that worked.

Thank you very much I would not have been able to fix this problem without the help you gave me.

> **tripolitan said:**
> Everything looks normal, sda4 is an extended partition (extended=logical and not to be confused with the Second Extended file system, they are different things) the size of /dev/sda4 is exactly what it should be (the sum of all partitions that were created within it)

There are several ways to fix this, the easiest is to edit fstab and reboot.
For swap to work, your fstab should look like this (comment out the uuid stuff):

proc /proc proc defaults 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 / ext3 relatime,errors=remount-ro 0 1
/dev/sda7 none swap sw  0       0 

otherwise, major file system surgery is needed to rectify this mess. If this is a new, un-upgraded install, I would suggest re-installing but taking extra care in partitioning. (with 4GB RAM, you do not need all that swap)

---

