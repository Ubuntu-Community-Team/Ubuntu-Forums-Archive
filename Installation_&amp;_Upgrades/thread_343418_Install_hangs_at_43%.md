---
title: "Install hangs at 43%"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by jt720 on 2007-01-21
Hi, I'm a long-time user of Windows and have been trying to make the switch over to Linux, specifically Edgy.  A couple weeks ago I had installed Edgy in a dual boot form with XP.  Everything worked fine except for my NVIDIA Geforce4 Ti 4200.  I tried many different approaches to get 3d working to no avail.  Yesterday, I decided to reinstall Ubuntu and start over, hoping that maybe I could get things going.  The problem is that my install hangs at 43%.  In addition to that install hanging, GRUB no longer works and I can't get into any installed OS.  I am running from the Live CD right now, which boots fine (sans 3d, of course.)

I had a 120GB ntfs drive that I had rearranged into a ~60/40 split, with Ubuntu on the smaller partition.  I am at a loss here.  All of my usual troubleshooting paths are geared for Windows.  I am thinking that I need to overwrite the MBR, but am having difficulty doing so (does LiveCD prevent the use of the CD drive for things other than the OS?)  Also, I tried using my XP pro CD to fix the MBR, but it doesn't recognize any hardware to write to.  Any help would be appreciated.

---

### Post by jt720 on 2007-01-21
My fdisk -l is below.  I'm following some other current threads that seem to have relevance, as well.








ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8583    68942916    7  HPFS/NTFS
/dev/sda2            8584       14117    44451855   83  Linux
/dev/sda3           14389       14593     1646662+   5  Extended
/dev/sda4           14118       14388     2176807+  82  Linux swap / Solaris
/dev/sda5   *       14389       14580     1542208+  83  Linux
/dev/sda6           14581       14593      104391   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by louieb on 2007-01-21
I spent the better part of yesterday trying to install Edgy on an old Dell Dimensions P3 w/ 256MB ram. Tried live live and alternate CD. Got it to install once and it froze up the first time I put a music CD in. This is not a dual boot machine. Said to heck with it and installed Kubuntu Dapper on it. Very smooth and easy install. I guess what I am trying to say is that Edgy has it problems.
 
Don't know why XP pro CD could not fix it, that the usual way to straighten out things so you can at least boot XP. Try the [Super Grub disk]("http://supergrub.forjamari.linex.org/") it is suppose to be able to fix the MBR to boot Windows.  The Dual Boot site in my signature also has some fix it stuff in it.

---

