---
title: "Setting up partitions for Linux and Windows with Parted Magic"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by pariate369 on 2010-11-17
Hi

I am using Parted Magic to set up partitions for multiple Linux OS installations to run alongside Windows.  I need a little help figuring out how to proceed!

The plan is to install OpenSUSE, Mint and Ubuntu (in that order, to try and avoid Grub problems).  My understanding is that:

[INDENT]* I need a / and a /home partition for each Linux distro 
* I only need one same swap partition
* apart from the swap, all partitions should be ext 4.[/INDENT]


I have attached a screenshot of the existing set up.  I'd be grateful if somebody could let me know if I've got the right idea please.  I know next to nothing about Linux, I am a noob!

Thank you.

EDIT - 

Partial results from Boot Info Summary


============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 439464928 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #9 for 
                       /boot/grub/menu.lst.

---

### Post by sikander3786 on 2010-11-17
Hi.

> I need a / and a /home partition for each Linux distro 

You don't need a separate /home partition. You can create one if you like but a minimum setup would be a / partition and a single Swap partition for all distros. Ext3 or Ext4 would work.

You have an existing installation of Ubuntu and Mint? Are you going to wipe them?

Just create the partitions in your extended drive for each distro. What else you want to know?

---

