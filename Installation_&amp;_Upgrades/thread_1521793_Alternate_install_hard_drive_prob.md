---
title: "Alternate install hard drive prob???"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Ojustaboo on 2010-07-01
I have 3 hard drives, two for windows 7 and a 750G for Linux.

It usually boots from the win7, but before attempting my ubuntu install, I changed it to boot from the linux drive, then started the alternate install from cdrom.  (Want grub to be on Linux drive and simply point to the windows drive when I need to boot windows)

I followed the instructions here

[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)

After the installation had completed, restarted the computer,  but when BIOS was finding my hard drives,  it hung as it was trying to identify my Linux drive. (it hung before I even got a chance to go into BIOS settings)

Powered off, tried again, same thing happened

Checked the cabling was fine, it was.

Pulled the SATA lead out of the back of my Linux drive, then all worked fine and I am now back in windows.  With windows up and running, have plugged back in the SATA cable and can see the Linux drive fine.  Have just deleted all Linux partitions from it from within windows and now it boots fine and finds all drives.

Any ideas what might be causing this please?

many thanks

(64 bit)

---

### Post by Ojustaboo on 2010-07-01
Tried another install, same problem.

Plugging it back in with windows running and going into windows disk management, it tells me the Linux drive has the following two partitions (which seem correct to me)

190MB Primary (/boot partition)  and 698 GB partition (LVM partition)

Deleted these partitions and once again, it now finds the drives fine.

Odd ???

---

### Post by Ojustaboo on 2010-07-01
This is making no sense to me. It's not getting as far as looking for boot records.

Just tried it again.

I have 3 hard drives.. 2 Samsung HD750LJ's  and 1 Samsung HD501LJ

One of the 750GB has win7 on it and the 500GB is NTFS
The other 750GB is where I installed Ubuntu onto a LVM.

I've tried both writing grub to the linux drive and writing it to the win7 drive, both caused the same problem and of course I then had to use the windows dvd to repair the windows MBR.

Everything installed, windows boot records on first hard drive, grub on 2nd hard drive, BIOS set to boot from second hard drive before I installed Ubuntu.

I reboot after install and it only gets this far before it hangs.
> 
Serial ATA AHCI BIOS Version iSrc 1.20E
Copyright (c) 2003 - 2008 Intel Corporation
** This version supports only Hard Disk & CDROM drives **
Please wait. This will take a few seconds

Controller  Bus#00,  Device#1F, Function#02: 06 Ports, 03 Devices
Port-00:  Hard Disk, SAMSUNG  HD753LJ
Port-01:  No device detected
Port-02:  No device detected


And it hangs there, doesn't get as far as trying to boot a disk.

I unplug the Hard Drive used for Ubuntu, try again, it boots into windows fine, I plug the Linux drive back in and Windows disk management can see it fine.

I reboot on the offchance, and it hangs in exactly the same place, again I remove it, boot into windows, re-attach it, but this time I delete the Linux partitions.

Now when I reboot, it boots fine and everything is seen

> 
Serial ATA AHCI BIOS Version iSrc 1.20E
Copyright (c) 2003 - 2008 Intel Corporation
** This version supports only Hard Disk & CDROM drives **
Please wait. This will take a few seconds

Controller  Bus#00,  Device#1F, Function#02: 06 Ports, 03 Devices
Port-00:  Hard Disk, SAMSUNG  HD753LJ
Port-01:  No device detected
Port-02:  No device detected
Port-03:  Hard Disk, SAMSUNG  HD753LJ
Port-04:  Hard Disk, SAMSUNG  HD501LJ
Port-05:  No device detected


Then it checks for a bootable CDROM as I have that set as first boot device, then it searches for boot records on the hard drive.

It's the weird fact that this is happening way before it's trying to boot from the drives that's totally confusing me.  3 times now it wont find the drive with Linux installed. Very very odd

---

### Post by darkod on 2010-07-01
What about plugging the second and third disks in another sata ports? It looks like your mobo/bios is not liking the disk, you say it doesn't even get to the boot process.

---

### Post by Ojustaboo on 2010-07-01
Thanks will give that a go tomorrow.

I just find it very odd that the BIOS finds the drives fine when I delete the Linux partitions but fails to find it when I install Linux.

I would have thought it would have not found it regardless of whether Linux was installed or not, but that doesn't seem to be the case.

There's also another SATA controller on my MB, a Gigabyte controller, if swapping to one of the unused normal ports doesn't solve it, I could give that one a go.

Might even just try swapping the cables so that the Linux disk is the first one found and see what happens then.

Will let you know how I get on tomorrow.

---

### Post by Ojustaboo on 2010-07-02
Odd, none of the South Bridge SATA 2 ports would accept the drive with  Linux installed (partitioned), but using the Gigabyte SATA 2 ports work  fine.

So I've got around that problem. Now to work out why the install keeps  hanging at 75%

---

