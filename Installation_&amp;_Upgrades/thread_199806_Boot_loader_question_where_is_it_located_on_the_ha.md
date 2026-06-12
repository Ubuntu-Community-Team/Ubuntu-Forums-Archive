---
title: "Boot loader question: where is it located on the hard disk and how to avoid deleting?"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by KillrBuckeye on 2006-06-19
I'm fairly new to Linux and dual-booting, and I want to make sure I understand how the boot loader works so I don't blow it away by accident.  On my main rig I have a dual boot with WinXP and Ubuntu 5.10.  WinXP is on its own physical drive (74GB Raptor), while Ubuntu is on another drive (320GB) with a bunch of partitions.  

Where is the GRUB bootloader actually located?  Does it reside in one of the existing disk partitions, or does it have reserved space on the drive that's not affected when the partitions are edited?  I'm asking because I use Acronis True Image to restore my Windows system partition from time-to-time, and I don't want to screw up my GRUB bootloader by doing this.  If I restore an image of my Windows partition that was made BEFORE I created the dual boot with Ubuntu, will I lose my boot loader?

Next question:  If I choose to do a fresh install of Ubuntu 6.06 instead of upgrading from 5.10, will it reinstall GRUB and automatically detect my Windows installation?  Basically I want to avoid rendering my Windows installation unbootable.  

Any help you could provide would be appreciated.  Thanks!

---

### Post by zxee on 2006-06-19
Referring to Knoppix Hacks, a book I highly recommend even if you're not interested in that distro, > The MBR is a 512-byte segment at the begining (the 1st sector) of a hard drive
In dos you restore this sector by doing fdisk /mbr. I don't use acronis so I can't help you there.
Ubuntu Dapper should see your windows install and create a grub entry for it.
Hope that helps.

---

### Post by tomchuk on 2006-06-19
[QUOTE=KillrBuckeye]I'm fairly new to Linux and dual-booting, and I want to make sure I understand how the boot loader works so I don't blow it away by accident.  On my main rig I have a dual boot with WinXP and Ubuntu 5.10.  WinXP is on its own physical drive (74GB Raptor), while Ubuntu is on another drive (320GB) with a bunch of partitions.  

Where is the GRUB bootloader actually located?  Does it reside in one of the existing disk partitions, or does it have reserved space on the drive that's not affected when the partitions are edited?[/quote]

IIRC It resides in the first 512 B of your primary boot drive (by default). This is not part of any partition, so screwing with partitions shouldn't affect it.

> I'm asking because I use Acronis True Image to restore my Windows system partition from time-to-time, and I don't want to screw up my GRUB bootloader by doing this.  If I restore an image of my Windows partition that was made BEFORE I created the dual boot with Ubuntu, will I lose my boot loader?

Acronis shouldn't touch the boot sector, but if it does it's easy enough to fix. Boot up with the installer CD or a LiveCD and run grub-install /dev/hda to fix things.

> Next question:  If I choose to do a fresh install of Ubuntu 6.06 instead of upgrading from 5.10, will it reinstall GRUB and automatically detect my Windows installation?  Basically I want to avoid rendering my Windows installation unbootable.

Either way it should just work. If it doesn't you can take a look at your current /boot/grub/menu.lst for the Windows entry and if it doesn't show up after a reinstall you can just add that entry yourself.

---

### Post by KillrBuckeye on 2006-06-22
[QUOTE=tomchuk]IIRC It resides in the first 512 B of your primary boot drive (by default). This is not part of any partition, so screwing with partitions shouldn't affect it.[/QUOTE]Thanks for the response.  Okay, in my situation my primary boot drive has only 1 partition with Windows installed.  My Linux installation is on a separate physical drive.  So my understanding is that Grub runs from the bootsector of my Windows drive, and then calls upon the /boot/grub/menu.lst file on my secondary drive.  Now my question is this:  What happens when I disconnect my secondary hard drive or blow away the Linux partition where the /boot/grub/menu.lst file?  Grub will try to load, but it won't be able to find the list file, so what can be done at that point?

---

### Post by tomchuk on 2006-06-25
Boot up with your Windows XP CD into the recovery console and run `fixboot` and `fixmbr` it will reinstall NTLDR to the MRB and everything should just work fine.

---

