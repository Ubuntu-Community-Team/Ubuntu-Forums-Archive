---
title: "Problems installing dual boot Ubuntu/Windows"
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by cannotinstall on 2017-02-23
I am trying to install Ubuntu 16.04.1 onto a laptop with an existing Windows 10 Home installation, intending to dual boot, and am getting the message "This computer currently has no detected operating systems" during the installation.  I've set the Boot Mode in the BIOS to Legacy, if that makes any difference.

I see the recommended solution seems to be [https://ubuntuforums.org/showthread.php?t=2108450&p=12486498#post12486498](https://ubuntuforums.org/showthread.php?t=2108450&p=12486498#post12486498) , but in there it says quite clearly that if I see a nice Ubuntu graphical screen when booting I should "**stop!!!**".  Okay, so I've stopped.  Where should I go from here?

I've tried the "something else" option in the "Installation Type" screen, and got the following:

[TABLE="width: 500, align: left"]
[TR]
[TD][SIZE=4][FONT=fixedsys]/dev/sda
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][SIZE=4][FONT=fixedsys]freespace
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]1MB
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][SIZE=4][FONT=fixedsys]/dev/sda1
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]fat32
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]272MB
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][SIZE=4][FONT=fixedsys]/dev/sda2
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]ntfs
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]16MB
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][SIZE=4][FONT=fixedsys]/dev/sda3
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]ntfs
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]477730MB
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][SIZE=4][FONT=fixedsys]freespace
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]472596MB
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][SIZE=4][FONT=fixedsys]/dev/sda4
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]ntfs
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]26843MB
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][SIZE=4][FONT=fixedsys]/dev/sda5
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]ntfs
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]1048MB
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][SIZE=4][FONT=fixedsys]/dev/sda6
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]ntfs
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]20646MB
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][SIZE=4][FONT=fixedsys]/dev/sda7
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]fat32
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]1048MB
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][SIZE=4][FONT=fixedsys]fresspace
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]
[/FONT][/SIZE][/TD]
[TD][SIZE=4][FONT=fixedsys]0MB
[/FONT][/SIZE][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
When I tried to use the 472596MB freespace area as ext4 and to "Install Now" it complained that "The partition table format in use on your disks normally requires you to create a separate partition for boot loader code.  This partition should be marked for use as a "Reserved BIOS boot area" and should be at least 1MB in size.  Note that this is not the same as a partition mounted on /boot."  So I thought to myself, "Okay, I'll use that 1MB of free space right at the start then, and tried to set that as a "Reserved BIOS boot area".  Uh uh.  I immediately got an error message saying "Unable to satisfy all the constraints on the partition."  Do what with a rubber hose?  What constraints?  How do I satisfy them?  Help (please)!

---

### Post by oldfred on 2017-02-23
What brand/model system?

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Do not run any autofix until someone has reviewed report.
And be sure to boot in correct mode, either UEFI or BIOS to match Windows 10 which looks like it is UEFI.

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

