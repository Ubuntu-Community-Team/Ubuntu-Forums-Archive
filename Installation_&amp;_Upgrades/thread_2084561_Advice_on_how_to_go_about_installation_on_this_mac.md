---
title: "Advice on how to go about installation on this machine"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by aramiis on 2012-11-15
hi there,

I recently got a new laptop and would like to dual boot like i did on my old one (which was windows xp and ubuntu)
new laptop has windows 7 and in considerably better than my old one (and more complicated it seems) and to be honest is confusing me slightly.

laptop info: 
ASUS K55VD,
x64 based,
6GB ram,
intel i7-3610QM,
BIOS version: american megatrends inc. k55vd.304 

first problem is i'm not sure how to partition up the hard drive, mainly cause it already has four primary partitions: efi system partition, OS (C:), DATA (D:) and recovery partition

my other issue is i don't know how big to make the partitions, the reason I have a new laptop is I've just started an architecture uni course this means I need to run certain programs on windows that i would think take up more more room than the average (notably autodesk's autoCAD and adobe CS6 programs) so any advice on that would also be appriciated

---

### Post by darkod on 2012-11-15
I don't use UEFI but I can give you few pointers that you can use to investigate further:
1. Since you have EFI system partition and win7, that means the hdd has GPT partition table which means the 4 partitions limit doesn't apply. You can create as many partitions as you want. You just need to create unallocated space first (not belonging to any partition).

2. To install ubuntu in UEFI mode you will need to use the 64bit version (which you should use with 6GB of memory anyway) AND make sure you boot the ubuntu cd/usb in UEFI mode. If you don't do that, it will try to install in the older legacy bios boot and you won't have an UEFI dual boot.

---

### Post by aramiis on 2012-11-15
> **darkod said:**
> I don't use UEFI but I can give you few pointers that you can use to investigate further:
1. Since you have EFI system partition and win7, that means the hdd has GPT partition table which means the 4 partitions limit doesn't apply. You can create as many partitions as you want. You just need to create unallocated space first (not belonging to any partition).

Ah thank you, that makes partitioning much simpler I hadn't realised I could do that.

> 2. To install ubuntu in UEFI mode you will need to use the 64bit version (which you should use with 6GB of memory anyway) AND make sure you boot the ubuntu cd/usb in UEFI mode. If you don't do that, it will try to install in the older legacy bios boot and you won't have an UEFI dual boot.

thanks again I will make sure to, and yes was planning to use the 64bit version

---

### Post by oldfred on 2012-11-15
+1 on Darko's comments

Still use Windows to shrink the Windows partition, but do not use it to create any partitions as Windows does not recognize Linux partitions.

Grub still has a bug in its os-prober. It creates a BIOS style chain boot entry for Windows not the newer efi. But you can download Boot-Repair and it will add the correct entry or you can manually add the correct entry to 40_custom or 25_custom as Boot-Repair does. You can install Boot-Repair to your install CD or flash drive or download a full Repair ISO.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

More reference info if interested.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

Installs that worked with a little help.
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

I think these were Asus motherboard, so not sure they apply. And the newest versions of Ubuntu work much better with UEFI. Most bugs resolved.
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)

---

