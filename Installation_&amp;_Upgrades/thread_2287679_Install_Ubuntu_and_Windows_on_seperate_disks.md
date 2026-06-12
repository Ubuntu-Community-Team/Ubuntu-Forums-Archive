---
title: "Install Ubuntu and Windows on seperate disks"
date: 2015-07-21
forum: Installation &amp; Upgrades
---

### Post by ryu kun on 2015-07-21
I have a notebook computer with two SSD's and one HDD.

I want to install Ubuntu 14.04 and Windows 8.1 on separate SSD's and keep HDD as a common data disk.

My computer has UEFI and legacy bios options.

I have never installed two OS's on independent disks and I did not do any Ubuntu installation on UEFI before. So maybe it is best to ask first than trying and making the system unusable. :)

How can I do this?

---

### Post by yancek on 2015-07-21
You need to install both as UEFI OR both as BIOS/MBR.  Mixing will lead to all kinds of problems.
When you install windows, just have the SSD you want to use attached.  The methods to use are different for UEFI and BIOS/MBR installs so that is your first decision.  If you have not used Linux before, you need to familiarize yourself with the drive/partition naming conventions as they are different from windows.

---

### Post by oldfred on 2015-07-21
Since UEFI & BIOS are not compatible, how you boot installer is then how it installs for both Windows & Ubuntu. Not sure exactly how Windows does it or how you know for sure.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

In UEFI boot tab menu you should see two entries for booting flash drive. One clearly UEFI:name and other just :name where name is brand name or label on flash drive. The one with just name is then the CSM/BIOS/Legacy boot mode.

Attached shows a Toshiba flash drive that one user posted.

Disconnecting drive may cause UEFI entry to be lost but easily re-added. 

I have installed Ubuntu to sdb drive with another copy of Ubuntu on sda. And even though it told me it was installing grub2 boot loader to sdb, it installed to sda. With UEFI that is not an issue as Windows & Ubuntu have separate folders in an efi partition for booting.

       You will need to use the 64 bit version of 14.04 or 15.04 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need Windows  fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by ryu kun on 2015-07-22
Thank you for your replies.

I have successfully completed installation by reading the document you linked.

To summarize:

1. Install Windows 8.1 to SSD 2, by using disk image written to USB flash disk via Rufus.
2. Install Ubuntu 14.04.2 to SSD 1, by using disk image written to USB flash disk via Rufus. 
a) During installation, choose "Something else" on partitioning phase. Keep first two partitions in the SSD 1 as they are (EFI and first small NTFS partitions created by Windows installation).
b) Created two additional partitions for / and /home mount points. 
c) Created a swap partition as well.
d) Linked my HDD to /windows mount point.
e) Rest is the same Ubuntu installation.

Result: GRUB installed successfully with 4 options:
1. Ubuntu
2. Advanced settings for Ubuntu (or something like that)
3. Windows boot manager
4. System setup

When I choose the first, Ubuntu boots.
When I choose the third, Windows boots.

---

