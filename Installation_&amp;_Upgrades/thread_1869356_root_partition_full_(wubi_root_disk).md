---
title: "/root partition full (wubi root disk)"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by cintomail on 2011-10-25
I have installed ubuntu inside windows using wubi and now my /root partition is almost full so i cant do an upgrade. I have set ubuntu size to 3 gb while installation so clearing logs or files wont help.

Is there any other way to increase the size of wubi root disk. 

Please help..

---

### Post by bcbc on 2011-10-25
3gb is the absolute minimum (prior to 11.10 where it's 5GB) - not much you can do with 3 GB.
[HOWTO: Resize the WUBI virtual disk]("http://ubuntuforums.org/showthread.php?t=1625371")

---

### Post by critin on 2011-10-25
I would save personal files/pics, music, on a cd or flash, uninstall Wubi through the uninstall windows program and reinstall ununtu with a live cd or usb flash "side by side" windows.  You have room on your disk? 20g or more?

3 g's is barely large enough for the os, not counting all the updates and other things you'll want to add.  *It's tiny*.

---

### Post by Mark Phelps on 2011-10-26
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

