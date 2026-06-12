---
title: "Partitions &amp; Filesystems help"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by bradders on 2011-11-09
Hi, I'm from an AIX background so used to Volume Groups containg Logivcal Voumes with Filesystems on top. Just installed Ubuntu 11.04 desktop with defaults onto a PC and want to create some filesystems. A "df -m" shows me that it looks like the FS /dev/sda1 has almost all of the disk.

```
[INDENT]bradders@ubuntu-desktop:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda1                36848      4867     30110  14% /
none                       368         1       368   1% /dev
none                       375         1       374   1% /dev/shm
none                       375         1       375   1% /var/run
none                       375         0       375   0% /var/lock
[/INDENT]
```An "ls /dev/sd*" shows me the available devices.[INDENT]```
bradders@ubuntu-desktop:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5[/INDENT]
```Not sure what these are exactly so thought I'd try and create a FS on /dev/sda1 but that is (assumedly) the FS, which makes sense[INDENT]```
bradders@ubuntu-desktop:~$ sudo mkfs.ext3 -L /newfs /dev/sda1
[sudo] password for bradders: 
mke2fs 1.41.14 (22-Dec-2010)
/dev/sda1 is mounted; will not make a filesystem here!
```[/INDENT]So I thought I'd try making the FS on /dev/sda but then I get the following;[INDENT]```
bradders@ubuntu-desktop:~$ sudo mkfs.ext3 -L /newfs /dev/sda
mke2fs 1.41.14 (22-Dec-2010)
/dev/sda is entire device, not just one partition!
Proceed anyway? (y,n)
```[/INDENT]I guess I'm being pretty dumb here. What I really wanted to do was have (in AIX terms) the whole disk as one VG, then create new filesystems on that VG as required, allocating the necessary space to each one. How do I acheive this here? TIA :confused:

---

### Post by Gatemaze on 2011-11-09
I don't know aix or volume groups but it sounds to me like you want one extended partition with many logical partitions in it. A tool like gparted can help you with it. You will have to unmount the partition so you will have to run gparted from a livecd.

---

### Post by coffeecat on 2011-11-09
Hi

> **bradders said:**
> A "df -m" shows me that it looks like the FS /dev/sda1 has almost all of the disk.

Judging by your ls /dev/sd* output, that's probably so.

> **bradders said:**
> An "ls /dev/sd*" shows me the available devices.[INDENT]```
bradders@ubuntu-desktop:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5[/INDENT]
```Not sure what these are exactly

/dev/sda is the whole physical disk. df -m tells us that /dev/sda1 is your root partition. /dev/sda5 is a logical partition by definition, and knowing the Ubuntu installer I'd hazard a guess that's your swap partition. Which would make sda2 an extended partition. But to be sure, post the output of:

```
sudo fdisk -lu
``` 

> **bradders said:**
>  so thought I'd try and create a FS on /dev/sda1 but that is (assumedly) the FS, which makes sense

Not quite. /dev/sda1 is a partition which contains a filesystem, most probably ext4 which has been the default for Ubuntu for a couple of years now.

> **bradders said:**
> So I thought I'd try making the FS on /dev/sda but then I get the following;[INDENT][CODE]bradders@ubuntu-desktop:~$ sudo mkfs.ext3 -L /newfs /dev/sda
mke2fs 1.41.14 (22-Dec-2010)
/dev/sda is entire device, not just one partition!

You can make a filesystem in a drive, it's a bit messy imo, but you shouldn't here since you already have partitions with filesystems.

> **bradders said:**
> What I really wanted to do was have (in AIX terms) the whole disk as one VG, then create new filesystems on that VG as required, allocating the necessary space to each one. How do I acheive this here? TIA :confused:

LVM would be the answer but since I've steered clear of this I'm not qualified to help. 

Let's rephrase the problem. What exactly are you trying to do? Why do you want logical volumes or their equivalent? Perhaps conventional partitions as the previous poster suggests would fit the bill. Let's have a look at your fdisk output and what you want to achieve.

---

### Post by dino99 on 2011-11-09
a standard installation looks like:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by darkod on 2011-11-09
For LVM (and/or RAID) you DON'T use the standard ubuntu desktop cd. You use the alternate cd. That has a text based installer (similar to old XP type), not GUI, bit it installs the same system as the desktop cd. The difference is that the alternate cd has built in support for LVM and RAID.
Since this is a new install it's much easier to re-install using the alternate cd than trying to add LVM now (not sure if it's possible at all).
And if you want more control of your partitioning you always choose manual partitioning, none of the auto options, regardless of what OS we are talking about. That way you select the sizes of the partitions.

As the other post said, dev/sda is the whole disk, /dev/sda1 is your ext4 root (it already has a FS), /dev/sda2 is extended partition and /dev/sda5 is the swap partition inside it.

---

### Post by bradders on 2011-11-17
> **bradders said:**
> Hi, I'm from an AIX background so used to Volume Groups containg Logivcal Voumes with Filesystems on top. Just installed Ubuntu 11.04 desktop with defaults onto a PC and want to create some filesystems. A "df -m" shows me that it looks like the FS /dev/sda1 has almost all of the disk.

```
[INDENT]bradders@ubuntu-desktop:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda1                36848      4867     30110  14% /
none                       368         1       368   1% /dev
none                       375         1       374   1% /dev/shm
none                       375         1       375   1% /var/run
none                       375         0       375   0% /var/lock
[/INDENT]
```An "ls /dev/sd*" shows me the available devices.[INDENT]```
bradders@ubuntu-desktop:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5[/INDENT]
```Not sure what these are exactly so thought I'd try and create a FS on /dev/sda1 but that is (assumedly) the FS, which makes sense[INDENT]```
bradders@ubuntu-desktop:~$ sudo mkfs.ext3 -L /newfs /dev/sda1
[sudo] password for bradders: 
mke2fs 1.41.14 (22-Dec-2010)
/dev/sda1 is mounted; will not make a filesystem here!
```[/INDENT]So I thought I'd try making the FS on /dev/sda but then I get the following;[INDENT]```
bradders@ubuntu-desktop:~$ sudo mkfs.ext3 -L /newfs /dev/sda
mke2fs 1.41.14 (22-Dec-2010)
/dev/sda is entire device, not just one partition!
Proceed anyway? (y,n)
```[/INDENT]I guess I'm being pretty dumb here. What I really wanted to do was have (in AIX terms) the whole disk as one VG, then create new filesystems on that VG as required, allocating the necessary space to each one. How do I acheive this here? TIA :confused:
Thanks for your help folks - I've now used gparted on a CD to reduce the sda1 down to 10 GB and now have 30 GB of free space. I think LVM is the right way forward and more akin to what I'm used to in AIX, so I'm reading up on this now

---

