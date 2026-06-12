---
title: "Dual boot Windows 10 on non-UEFI hardware"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by Gary_Wood on 2015-08-17
I am trying to dual boot the latest build of Ubuntu alongside Windows 10 on old hardware that is not UEFI.

I've created a bootable USB of the Ubuntu installer files, and my computer successfully boots from this. However, when I get to the point of the installation that asks me to select the installation location, it says no existing operating systems have been detected, and I don't see the free space I've created to install Ubuntu to.

Searching online suggests that this is because UEFI is enabled, but I'm almost certain this is not the case because I can't find an option in the BIOS, and the computer is from 2009.

What can I do?!

---

### Post by yancek on 2015-08-17
Which Installation Type did you select in Ubuntu?  How did you create the free space, using the Disk Management tool in windows?  Since you can boot the Ubuntu install medium, do that and open a terminal so you can get drive/partition info to post here.  Use the command:  sudo fdisk -l(Lower Case Letter L in command).

---

### Post by oldfred on 2015-08-17
Windows 8 or later, has the fast startup setting whether UEFI or BIOS install.
That setting is really just hibernation and must be off if installing any other operating system even another copy of Windows.

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

The Linux NTFS driver will not mount a NTFS partition that is hibernated or if needing chkdsk to prevent damage that a chkdsk could then not fix.

Best to resize Windows using Windows disk tools and reboot immediately to let it run chkdsk which is required after any resize. Make sure fast start up is off. 
Then install Ubuntu into unallocated space.

If BIOS make sure you have not used all 4 primary partitions, and do not create partitions in Windows or it may convert to its proprietary dynamic partitioning which does not work with Linux.
Post current partitioning from Ubuntu installer as suggested by yancek, so we can confirm current partitioning.

---

