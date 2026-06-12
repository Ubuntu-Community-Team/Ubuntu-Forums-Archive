---
title: "GParted reporting unallocated space for drive with Ubuntu and NTFS partitions"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by daniel_szollosi-nagy on 2007-05-17
Hi there,

I apparently did something very stupid and seem to have messed up partitioning information. I initially erased two NTFS partitions to make room for Ubuntu, then created a 30GB one for Ubuntu and 10GB for Windows. I installed Ubuntu first, used it for a couple of days and then wanted to install XP to compare some game fps under wine and native win32.

The Windows setup was told to install to the 10GB partition and it predictably nuked grub. However, the Windows installer wouldn't boot after it finished formatting and copying the installation files. I fixed grub and could boot into Ubuntu, but when I wanted to check on my partitions, I got this:

[IMG]http://img291.imageshack.us/img291/3030/screenshotdevsdagpartedej0.png[/IMG]

Now I know I have four partitions there, Ubuntu's home and the swap, a half-finished Windows setup that the installer couldn't boot into and a 120GB NTFS partition with my stuff on it, which I could mount from Ubuntu. Right now it's set as read only because I don't want to lose anything on it.

Anyone has any ideas as to why GParted is misreporting drive usage? And perhaps any ideas on getting the stupid Windows installer to finish setting that thing up?

Thanks,

Daniel

---

### Post by daniel_szollosi-nagy on 2007-05-17
Anyone?

---

### Post by merlinus on 2007-05-17
Is it possible that your windows install decided to take over the entire hard disk, despite your choosing otherwise?  

Then when it crashed, it left one huge unallocated partition.

Perhaps you already did this, but can you boot from a gparted live cd to have another look?  

Good luck!

-merlin

---

### Post by daniel_szollosi-nagy on 2007-05-22
I didn't want to muck about with this as long as Ubuntu booted from the partition GParted said was unallocated... but I'm worried this could get worse, so I'd rather find out what is behind all this and fix it for good.

I just booted from the live CD and got the same unallocated screen as above. Here's the output from an fdisk -l

> ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20022   160826683+   f  W95 Ext'd (LBA)
/dev/sda2   *        5101       20022   119860933+   7  HPFS/NTFS
/dev/sda5               1         249     1999998   82  Linux swap / Solaris
/dev/sda6             250        3819    28675993+  83  Linux
/dev/sda7            3820        5100    10289601    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   42  SFS

I can see /dev/sdb fine under GParted. In fact, I can even mount the NTFS partition at sda7, and the live CD appears to be using the swap at sda5.

I'm stumped.

---

### Post by daniel_szollosi-nagy on 2007-05-23
Running [FONT="Courier New"]sudo parted -s /dev/sda unit cyl print[/FONT] told me: 

Error: Can't have overlapping partitions.

So I'm getting close to finding out what's wrong. The problem is I don't have a place to back up my 120GB NTFS partition - if I did, I'd just nuke the whole disk and start it all over again.

Is there any way to fix this problem without having to reformat the drive? Thanks!

---

### Post by Brinstar on 2007-05-23
> **daniel_szollosi-nagy said:**
> Running [FONT="Courier New"]sudo parted -s /dev/sda unit cyl print[/FONT] told me: 

Error: Can't have overlapping partitions.

So I'm getting close to finding out what's wrong. The problem is I don't have a place to back up my 120GB NTFS partition - if I did, I'd just nuke the whole disk and start it all over again.

Is there any way to fix this problem without having to reformat the drive? Thanks!

i had this exact same problem when i used gparted to setup my HD to install Zenwalk on it. I sorted my drive out by using the Zenwalk install-time partition utility.

gparted is total crap, sorry.

---

### Post by monti on 2007-05-25
You can probably work around your problem by using TestDisk, look here: [http://ubuntuforums.org/showthread.php?p=2486121#post2486121](http://ubuntuforums.org/showthread.php?p=2486121#post2486121) 

The bug is located in gparted's subsystem, libparted: [http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14](http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14)

---

