---
title: "Live CD to USB partiton."
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by jwhirl06 on 2012-10-23
Is is possible to install ubuntu to a USB partition (/dev/sdc5) with the usb key being (/dev/sdc)? I have a separate partition that contains maintenance tools for my work and one for an ubuntu distro. The startup disk creator will not let me direct it to a certain partition.

---

### Post by oldfred on 2012-10-23
Do you want the installer or a full install in sdc5?

Most of the install utilities assume a smaller flash drive like 1 to 4GB and reformat the entire drive. But if you have or can have grub2's boot loader in the MBR then you can directly boot an ISO with loopmount. I have multiple ISO on one flash drive and in one hard drive to install on other drives.

Hard drive:

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by jwhirl06 on 2012-10-23
> **oldfred said:**
> Do you want the installer or a full install in sdc5?

Most of the install utilities assume a smaller flash drive like 1 to 4GB and reformat the entire drive. But if you have or can have grub2's boot loader in the MBR then you can directly boot an ISO with loopmount. I have multiple ISO on one flash drive and in one hard drive to install on other drives.

Hard drive:

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

I'd like to get the full install into sdc5, I just can't figure out how to install it to sdc5. Or get grub onto it, sorry I am a bit new at getting this involved.

---

### Post by oldfred on 2012-10-23
I thought you were trying to boot the installer CD or USB?

A full install to any second drive whether SATA, USB, hard drive or flash is really just the same.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

You have to use manual install or Something to get that option on where to install the grub2 boot loader. And you want it in the MBR of the second drive not in any partition.

---

### Post by C.S.Cameron on 2012-10-23
Set up your drive partitions using gparted.
Remember only four primary partitions are allowed, sdc5 indicates a need for an extended partition.

If it is not a problem disconnecting the internal drive do it.

Boot the installer.

When you get to partitioning make sure sdc is selected for the install.

At "Installation type" select "Something else". 
Confirm Device is correct.
Select new partition table.

You should see the current partitions on the drive.
double click the one you wish to install to.

Select "Primary", "New partition size ..." = xxxx megabytes, Beginning, Ext4, and Mount point = "/" then OK.

Confirm "Device for boot loader installation" points to the USB drive, (sdc not sdc5).

Click "Install Now".

---

