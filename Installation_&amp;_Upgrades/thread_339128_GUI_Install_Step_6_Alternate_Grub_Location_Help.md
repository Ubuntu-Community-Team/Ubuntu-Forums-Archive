---
title: "GUI Install Step 6 Alternate Grub Location Help"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by Archalien on 2007-01-15
I am trying to install Ubuntu to a partition of a hard drive but cannot have grub install to the MBR.  In step 6 of the graphical install of edgy it allows you to change the location. The default (MBR) is shown as "(hd0)".

I partitioned my drive and ubuntu is/will reside on /dev/sda2
--Windows already on /dev/sda1 swap on /dev/sda3......
as reported in the "Prepare partions"(1st step) of manual editing w/ gparted
In (part 2) "prepare mount points" it lists the partition as:
"Partition 2 Disc USB/SCSI/SATA 1 (Primary) [sda2]"        it is a SATA hdd
Then at stage 6 it says:
"Grub will be installed to (hd0)"   with the option to change "(hd0)"
Selecting the change option provides a dialog box titled "Device for boot loader installation"  with a text entry field
I have tried "(sda2)" and "(/dev/sda2)" and "(hd0,2)" all of which fail.



but I cannot find the proper syntax that allows the installer to place grub on this partition rather than the MBR. The installer always fails with no real indication of the error and a dump of the call stack which was pretty useless to me.

Dapper required the alternate install disc to accomplish this, but Edgy allows for this in the graphical install.

[here is a sample picture]("http://debianadmin.com/copper/displayimage.php?pid=755&fullsize=1") of the step Im stuck at, although not an actual sceen shot from my computer it is representative.
At the bottom you see a list of partitions to be formatted. Mine reads"
"partition #2 of SCSI1 (0,0,0) (sda) as ext3" Wonder if this info is helpful that its listed as SCSI1??

Installation fails at 94% with a dialog box titled "Unable to Install GRUB in (hd0,4)" saying "Executing 'grub-install (hd0,4)' failed. This is a fatal error.


Can someone help me with the syntax required for this option.
I just need to know what exactly to put in the Step 6 option box to have it install grub on the 2nd (ubuntu) partition.

thx

---

### Post by Archalien on 2007-01-15
Solved

"/dev/sda2" worked, I just had to omit the ( ) found in the feault (hd0) example.

---

