---
title: "harddrive wipe"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by natholego11 on 2010-12-17
do i need to wipe my harddrive prior to installing Xubuntu?  cause when i go to install it it gives me some errors such as

mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error 
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

and i am not sure at this point how to be beyond this.

---

### Post by mr clark25 on 2010-12-17
looks like the install disk is bad. did you try checking it for errors?

---

### Post by natholego11 on 2010-12-17
> **mr clark25 said:**
> looks like the install disk is bad. did you try checking it for errors?

no, when i try it will prompt me with "unreadable disk" 

whats the best way to burn the disk on OSX, i am installing it on a pc i made.

---

### Post by mr clark25 on 2010-12-17
sorry for not being more specific. i meant the "check disk for defects" option when you boot from it.

if it is a 10.04 or 10.10 disk, you will need to press a key while the icon (a stangle little stick figure with a keyboard next to it) is displayed to bring up the menu.

---

### Post by Pillars of Creation on 2010-12-18
natholego11,

“do i need to wipe my harddrive prior to installing Xubuntu? cause when i go to install it it gives me some errors such as”

I understand what you’re asking but you’re using the term wiping the disk incorrectly. Wiping is the process of writing zeros and ones to the disk to prevent data on the disk from being found by some form of digital detective. A free program called Eraser or Clean Disk Security can do that from within Windows. Really the best way to wipe the disk clean is to hold with vice grips and drill a hole through it. Then take it out back, pour gasoline on it, and light it on fire.

What you want to do is make the disk like new. There are two ways to do this. One is to do a full format or a low level format. If you happen to have a Windows XP disc that has any of the three service pack slipstreamed into it, you can you use this disc and start the Windows XP install procedure. When it comes to selecting a partition simply select the entire hard drive and do a full format. Do not do a quick format. You can go ahead and install Windows. Allow 3 to 4 hours. After that is done boot a Ubuntu disc and run Ubuntu from the desk. Use the Gparted partition utility to delete the Windows partition and make whatever partitions you want.

The problem with the Gparted partition utility is it does not seem to have the ability to a full or low-level format. What this procedure is doing is checking all the sectors or blocks on the disk and marking any ones that are bad as bad. It also erases the master boot record and any traces from a prior operating system install.

The other way to accomplish the same thing is to download the ISO image from the hard drive manufacturer and make a bootable CD diagnostic disk. Both the major manufacturers such as Western Digital and Seagate offer such a disc. The full diagnostic test should accomplish the same thing. The other nice thing about the diagnostic disk is that you can run it on a system that is populated what OS’s without blowing them away.

“whats the best way to burn the disk on OSX, i am installing it on a pc i made.”

Burn an ISO image to CD on Mac OS X

1. Start the Mac OS X Disk Utility (click Applications, then Utilities, then Disk Utility).
2. Drag your ISO icon to the left sidebar of the Disk Utility application. (Figure 1 below.)
3. On that left sidebar, select the ISO you just created.
4. From the menu bar choose Images, then Burn...
5. You're prompted to insert a disk, as shown in Figure 2 below.
6. After inserting the disk you're prompted one more time to proceed with the burn (Figure 3).

[http://www.devdaily.com/blog/post/mac-os-x/burn-iso-image-cd-on-mac-os-x](http://www.devdaily.com/blog/post/mac-os-x/burn-iso-image-cd-on-mac-os-x)

---

