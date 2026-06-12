---
title: "Ubuntu Install On Existing Win XP with RAID 0"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by |ShooZ| on 2008-09-10
I thought I'd give Ubuntu a try to get familar with a UNIX OS.  But now I fear I have completed hosed my computer.  Here's my story...

[PreInstall] Running Windows XP SP3 with RAID 0 on 2 hard drives.  (RAID 0 was the "hip" thing to do when I got this computer). I load the .iso disk and boot to it.  I elect to install Ubuntu and it asks where to create its partition.  There are 2 options: HD1 and HD2.  I chose HD1.  The rest of the install completes fine (as far as I can tell).

[PostInstall] My computer restarts and I get a Grub 5 error (indicating a partition problem).  I start to wonder where my Windows boot option is at.  From what I can tell my Windows partitions seem to be messed up.  I try running the Windows install CD and it shows 3 partitions now exist.  There was originally only 1 (for Windows).  

What is my best course of action for restoring my original Windows partition to recover any documents (afraid I already know the answer).

I'm sure I need to provide my information to help find a resolution, so please let me know what to give you guys.

Thank you in advance,
"A desparate Ubuntu explorer"

---

### Post by confused57 on 2008-09-10
> **|ShooZ| said:**
> I thought I'd give Ubuntu a try to get familar with a UNIX OS.  But now I fear I have completed hosed my computer.  Here's my story...

[PreInstall] Running Windows XP SP3 with RAID 0 on 2 hard drives.  (RAID 0 was the "hip" thing to do when I got this computer). I load the .iso disk and boot to it.  I elect to install Ubuntu and it asks where to create its partition.  There are 2 options: HD1 and HD2.  I chose HD1.  The rest of the install completes fine (as far as I can tell).

[PostInstall] My computer restarts and I get a Grub 5 error (indicating a partition problem).  I start to wonder where my Windows boot option is at.  From what I can tell my Windows partitions seem to be messed up.  I try running the Windows install CD and it shows 3 partitions now exist.  There was originally only 1 (for Windows).  

What is my best course of action for restoring my original Windows partition to recover any documents (afraid I already know the answer).

I'm sure I need to provide my information to help find a resolution, so please let me know what to give you guys.

Thank you in advance,
"A desparate Ubuntu explorer"

First thing you could try is boot the XP install cd, press "r", then enter FIXMBR.  See if this restores your ability to boot Windows.

If this doesn't work, boot the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), and post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"
This will show your current partitions on your drives.

---

### Post by tangibleorange on 2008-09-10
yeah also did you install with the Live CD or Alternate (text-based) CD. only the Alternate CD has proper RAID support.

---

### Post by |ShooZ| on 2008-09-10
First let me say **thank you** both for the quick, helpful responses.  After this happened, I had a horrible feeling I just lost the last 6 months worth of pictures, music, etc.  I know I'm no where near out of the woods yet, but you've given me hope.  Ok, without further ado..

> **confused57 said:**
> First thing you could try is boot the XP install cd, press "r", then enter FIXMBR.  See if this restores your ability to boot Windows.
I did try this after it happened.  I don't recall what the exact response was when I attempted to reboot, but it was something along the lines of "Operating system not found".  Ahh if the solution were only that simple =)

> **confused57 said:**
> If this doesn't work, boot the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), and post the output of:
```
sudo fdisk -l
```
I am able to load Ubuntu via the .iso when I make the selection "Try Ubuntu without any changes to your computer".  From there the output from your suggested terminal command is:
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18657   149862321   83  Linux
/dev/sda2           18658       19452     6385837+   5  Extended
/dev/sda5           18658       19452     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

> **tangibleorange said:**
> yeah also did you install with the Live CD or Alternate (text-based) CD. only the Alternate CD has proper RAID support.I tried to trace back my steps for which version I downloaded.  From the download tab on [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) I left both the radio buttons at default and downloaded "Ubuntu 8.04 LTS Desktop Edition - Supported to 2011".  The file name is "Ubuntu 8.04.1 i3.iso"

Thank you again for you help,
"An optimistic Ubuntu Explorer"

---

### Post by tangibleorange on 2008-09-11
> **|ShooZ| said:**
> First let me say **thank you** both for the quick, helpful responses.  After this happened, I had a horrible feeling I just lost the last 6 months worth of pictures, music, etc.  I know I'm no where near out of the woods yet, but you've given me hope.  Ok, without further ado..


I did try this after it happened.  I don't recall what the exact response was when I attempted to reboot, but it was something along the lines of "Operating system not found".  Ahh if the solution were only that simple =)


I am able to load Ubuntu via the .iso when I make the selection "Try Ubuntu without any changes to your computer".  From there the output from your suggested terminal command is:
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18657   149862321   83  Linux
/dev/sda2           18658       19452     6385837+   5  Extended
/dev/sda5           18658       19452     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

I tried to trace back my steps for which version I downloaded.  From the download tab on [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) I left both the radio buttons at default and downloaded "Ubuntu 8.04 LTS Desktop Edition - Supported to 2011".  The file name is "Ubuntu 8.04.1 i3.iso"

Thank you again for you help,
"An optimistic Ubuntu Explorer"

hmm that doesn't look good - fdisk doesn't report any windows partition on the first disk, and can't read the second.

My suggestion would be to download the Alternate CD from here:

[http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso]("http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso")

assuming you are using the x86 version (which you probably are if you selected the default options when downloading). then, when it gets to the partitioning stage, see what it shows.

---

### Post by Rorke on 2008-09-11
Hi, I have a similar problem - but I've managed (over several days) to destroy my partition table - but the data is all still there. I can't figure out how to use testdisk, and GParted doesn't seem to solve it. I have a live DVD Linux, but I don't know how to mount the original hard disk and use testdisk from it, or what to do with testdisk when I do.

Any ideas?
This seems fine - but the Brub loader says (from Super Grub Boot) unable to mount Error 17 for all the sections (apart from the XP, which I added in last thing lastnight which is error 12)


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3230    25944943+   7  HPFS/NTFS
/dev/sda2            3231       30401   218251026    f  W95 Ext'd (LBA)
/dev/sda5            3232       21295   145099080   83  Linux
/dev/sda6           28889       29645     6080571   82  Linux swap / Solaris
/dev/sda7           29646       30401     6072538+  82  Linux swap / Solaris

---

### Post by confused57 on 2008-09-11
I've never used Testdisk, so I can't help from personal experience, but maybe the instructions here can help:
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

Also from the same site are instructions for mounting various filesystems from Ubuntu:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by |ShooZ| on 2008-09-11
> **tangibleorange said:**
> hmm that doesn't look good - fdisk doesn't report any windows partition on the first disk, and can't read the second.

My suggestion would be to download the Alternate CD from here:

[http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso]("http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso")

assuming you are using the x86 version (which you probably are if you selected the default options when downloading). then, when it gets to the partitioning stage, see what it shows.Are you suggesting everything on my Windows side is lost forever?  Or should I download and install the Ubuntu version you linked with hopes of recovering my former OS?

*Edit*
OK.. I did some playing around with TestDisk.  I think my biggest problem exists because originally I was running RAID 0 on 2 separate HDD's which in turn had parts of the partition table on both HDDs making it even more difficult to recover... We shall see.

---

### Post by tangibleorange on 2008-09-12
sorry i really know nothing about RAID... maybe fdisk is not capable of accurately reporting RAID, i just don't know :S

---

### Post by |ShooZ| on 2008-09-14
Thank you everyone for the help.  After a week of research I've come to the conclusion that all is lost.  I've re-installed Windows and will be using the alternate Ubunto install this time around.

---

