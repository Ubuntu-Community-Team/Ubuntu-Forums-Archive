---
title: "Can't see harddisk in ubuntu installation."
date: 2015-09-04
forum: Installation &amp; Upgrades
---

### Post by devign on 2015-09-04
Hello,

I'm trying to install ubuntu next to my windows 7. 

I have one harddrive with 65GB of free space for my ubuntu install. I'm installing from a bootable USB drive, which works fine. 
However during my installation it can't find my harddrive, it only shows the USB drive. 

My drives SATA mode is RAID, I've tried to change it to IDE or AHCI, but then my windows 7 is unable to start anymore (also doesn't fix the missing harddrive problem in the installer).

I can run the ubuntu live mode from my USB drive, so I am able to use the terminal there. Is anyone able to help me out?


Screenshot of the installation where I can't find the harddisk.
[IMG]http://i58.tinypic.com/2u6d4kn.jpg[/IMG]


Screenshot of gparted, where the harddisk and it's partitions are visible:
[IMG]http://i61.tinypic.com/2ijgj7l.jpg[/IMG]

Thanks in advance,
Devign.

---

### Post by grahammechanical on 2015-09-04
What install option are you choosing? Install alongside? My advice would be to use the live session and Gparted to turn that unallocated space inside sda4 (the extended partition) into two logical partitions - one for Ubuntu and one for swap. Then use the Something Else option to install Ubuntu.

You have a BIOS boot system with a msdos partition table and that means there is a 4 primary partition limit on that hard disk and those 4 primary partitions are already used up. The extended partition counts as a primary partition. This is why the installer not showing any partitions. It cannot create the 2 Ubuntu partitions it needs.

Strange as it may seem, if the extended partition did not exist so that there were 3 primary partitions and 65GB unallocated space the installer might see that unallocated space and with your permission create an extended partition with 2 logical partitions inside to which Ubuntu would be installed. This is supposition on my part as I have not tested this theory.

Regards.

---

### Post by devign on 2015-09-05
I'm not allowed to choose an install option, probably because ubuntu doesn't recognize my harddisk, and therefore doesn't know there is a windows 7 install there.

I've deteled the extended partition in gparted, but unfortunately this doesn't solve the issue. I've also tried creating an extended partition with two logical partitions myself, one formatted ext4 and the other one linux-swap. This also did not work.

Gparted however gives me this error message, maybe that is the malefactor.

[ATTACH=CONFIG]264252[/ATTACH]

---

### Post by Bucky Ball on 2015-09-05
Welcome. Boot into Windows, switch off hibernation/fastboot (fast start?). If this is on, Ubuntu can't access the drive. Boot to the BIOS and switch off secure boot. If the machine came preinstalled with Win it is an EFI mode install. (sda1, in your screeshot, looks like the Win EFI partition).

RAID may be screwing with things. Did you install Win7 manually? 

Partition using 'Something Else' when you get to that section of installing Ubuntu. You'll see the Win partitions as NTFS partitions. Just don't go near them. You need free space, which you have. Resize Win partition with Win software and Linux with Linux if you need to. 

Backup prior to the install.

PS: Please attach screenshots by editing the post, click Go Advanced, and use the paperclip icon or 'Adv Reply' for new posts. Cheers. :)

---

### Post by devign on 2015-09-05
I've got Windows 7 enterprise via my university. It got one harddrive, and a 20GB mSATA cache, which is in RAID mode with the harddrive.

I'll try switching of the hibernation, fastboot, and secure boot. 

Thanks in advance.

EDIT: enabled hibernate seemed to be the problem, thanks all for the help!

---

