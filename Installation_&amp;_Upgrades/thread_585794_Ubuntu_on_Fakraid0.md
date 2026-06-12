---
title: "Ubuntu on Fakraid0"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by FnTm on 2007-10-21
So here I go again!

Hi all, im back, with more trouble.

I just got my pc connected to internet, and went straight for a copy of newest ubuntu, and tried installing it after [this]("https://help.ubuntu.com/community/FakeRaidHowto") walktrough. After just step 1, I reallized, that my Win partition was taking up my whole 80 gb RAID0 stripe, and i had to resize it, to fit my needs. But when I went to [this site]("http://gentoo-wiki.com/HARDWARE_Dell_Precision_690#Repartition_RAID0_Storage_Array"),to find out just how to do it, it started popping up some weird errors, like: (sorry for the long reading im going to put you trough im just very confused wright now...

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 40.0 GB, 40018599936 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee29ee29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 40.0 GB, 40018599936 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

**Disk /dev/sdb doesn't contain a valid partition table**
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdc

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5a91019

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

``` 

I tought that the line after my 2nd RAID drive, was kinda strange, but i continued on:
```
ubuntu@ubuntu:~$ sudo ntfsresize --info /dev/sda2
ntfsresize v1.13.1 (libntfs 9:0:0)
ERROR(2): Failed to check '/dev/sda2' mount state: No such file or directory
Probably /etc/mtab is missing. It's too risky to continue. You might try
an another Linux distro.
ubuntu@ubuntu:~$ sudo ntfsresize --info /dev/sda
ntfsresize v1.13.1 (libntfs 9:0:0)
Failed to startup volume : Invalid argument
ERROR(22): Opening '/dev/sda' as NTFS failed: Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong partition? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
if the disk was incorrectly repartitioned (see the ntfsresize FAQ).
ubuntu@ubuntu:~$ sudo ntfsresize --info /dev/sda1
ntfsresize v1.13.1 (libntfs 9:0:0)
Failed to load $MFT : Input/output error
Failed to startup volume : Input/output error
ERROR(5): Opening '/dev/sda1' as NTFS failed: Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.
ubuntu@ubuntu:~$ sudo ntfsresize --info /dev/sda2
ntfsresize v1.13.1 (libntfs 9:0:0)
ERROR(2): Failed to check '/dev/sda2' mount state: No such file or directory
Probably /etc/mtab is missing. It's too risky to continue. You might try
an another Linux distro.
ubuntu@ubuntu:~$ 

```

But this was just it... I stoped here , and didnt continue, because I was afraid to break something.

I allso did the [FakeRaidDebug]("https://help.ubuntu.com/community/FakeRaidDebug") and got the files, So im attaching them now.. maybe someone will know, what to do with them!

Thanks,
FnTm!

---

### Post by FnTm on 2007-10-22
Could someone help me plz?

P.S Sorry for the typo, ment FakeRaid

---

