---
title: "Live-CD Install Fails at Grub Install"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by mich1998 on 2007-10-27
I have searched the suggested forums with no help.

I have installed Debian, Slackware, SUSE, Arch, and Gentoo successfully form non-live-CD's (graphical installs I guess they're called.)  _**All have had grub installed on the root partition**_.

When I install grub into the root partition on these distro's they usually suggest the mbr (hd0), but allows you to install grub onto the root partion.  The first grub install usually fails, but the second attempt is always successful, without changing any numbers (I'm assuming that the distro's want to make sure that you really want to install grub on the root partition.)  In Gentoo, you have to run grub from the command line.

I have never been able to install off an Ubuntu or Kubuntu live-CD; The installations always error out at the point when grub is to be installed.  Also no luck with the Mint linux live-CD (which  I guess uses the same installer as the Ubuntu live-CD.

In the advance configuration on the live-cd's it always suggests (hd0) for the grub install option. I opt for the fourth partition, /dev/hda4, so I change (hd0)  to  (hd0,3).  94% through the install it aborts at the point where grub is being installed.  Is (hd0,3) the correct entry?  Is the partitioning scheme  the same as if you run grub from the command line?  Some help would be appreciated, and thanks in advance.  I really do hate live-CD's installs!

---

### Post by Pumalite on 2007-10-27
Assuming you have a Linux installed now, post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by khughitt on 2007-10-27
In the past I've had luck using the alternate install cd when running into similar problems during the grub installation. Another idea you could consider would be to try and run a cd with a newer testing (e.g. 2.6.23) kernel.. I don't think it would do the trick in this case since it's not much different from the kernel that ships with gusty, but sometimes the newer kernels have the hardware support you need. If you have another Ubuntu install, or a friend with u]Ubuntu, you can install the kernel on that machine and then use [Reconstructor]("http://reconstructor.aperantis.com/") to create a livecd with that kernel.

Goodluck!

---

### Post by mich1998 on 2007-10-27
Here is my fdisk partitioning scheme.  /dev/hda4 is the partition I try other distros on.  Used Partition Magic for original disk partitioning, and Boot Magic for booting the operating systems.  I always allow the new distro to re-format the partition when installing any new linux system.  Never have had any problems with any other non-live-cd distro.  Any suggestions?


Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

/dev/hda1   *          63     47118644     23559290+   b  W95 FAT32 (LBA)
/dev/hda2         47118645   188426384    70653870    f  W95 Ext'd (LBA)
/dev/hda4        47118645    81947501     17414428+  83 Linux
/dev/hda5        81947502    86156468     2104483+  82  Linux swap / Solaris
/dev/hda6   *    86156469    116728100     15285816 83  Linux

I see that Ubuntu has an alternate CD.  I"ll look to see if Kubuntu has an alternate CD,  too.  I do not think Mint linux has one.   I sure would like to be able to install off a live-CD, though.   That will probably be the way that most distros will install in the future.

Being that the install stops at grub install, (and assuming the system is fully installed except for grub) is there a way to install grub as a rescue operation from the live-CD, and then have an operational system?

---

### Post by logos34 on 2007-10-28
> **mich1998 said:**
> Being that the install stops at grub install, (and assuming the system is fully installed except for grub) is there a way to install grub as a rescue operation from the live-CD, and then have an operational system?

You can try [installing grub from live cd]("http://ubuntuforums.org/showthread.php?t=224351").  Except do 'setup (hd0**,3**)'

Also, only one partition should have the boot flag (*)

---

### Post by esagherardo on 2007-11-01
The problem seems to be the numbering of devices under grub on live-cd. Actually a bug of the live-install.

When live-cd is running, (hd0) may not be the HD. You must devise the number given to the HD, say e.g. (hd1); the actual number depends on your machine.

When installing, select "advanced" from the partitioner, and replace (hd0) with (hd1).

This allows to correctly install grub, up to one possible configuration error in the menu.lst. If the freshly installed system does not boot, you got this error, and you have to correct it.

The problem is that grub might number differently the devices when using the installed system instead of the live-cd. Let's say that, after reboot, your HD is (hd0); then /boot/grub/menu.lst  contains the wrong "root" entry, set to (hd1,1), which was used during the grub-install, and which should be (hd0,1).

To cope with, boot the live-cd, mount the physical device where /boot of the installed system is (not the /boot of the live virtual filesystem), cd into it, edit grub/menu.lst, change (hd1,1) into (hd0,1).

Warning: (hd0)(hd1)(hd0,1)(hd1,1) used here may be different on your system. 

Hope it helps.

Gherardo

---

### Post by Pumalite on 2007-11-01
Where is your menu.lst?

---

