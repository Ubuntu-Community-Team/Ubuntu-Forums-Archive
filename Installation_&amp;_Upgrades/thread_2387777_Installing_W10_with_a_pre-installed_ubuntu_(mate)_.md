---
title: "Installing W10 with a pre-installed ubuntu (mate) image"
date: 2018-03-23
forum: Installation &amp; Upgrades
---

### Post by gonzobilbao on 2018-03-23
Hi all,

First of all, hope there are not any duplicates. I have looked around  in older posts, but most of the questions are for ubuntu alongside a preinstalled W10... so I open a new thread. Sorry if there are any duplicates.

So for the longest time i have installed Windows (the last time, W10) and THEN ubuntu... all in UEFI mode (W10's default, even in older computers).  This gives many problems when updating W10, as it overrides the boot loader and either 1) you run boot-repair, 2) you manually tweak it (if boot repair doesn't work) or 3) you just do a key combination at start-up and manually boot into ubuntu. In one of my computers (the one at my work place!! :(   ) option 1 does not work, I don't want to be doing option 2 at every w10 upgrade (hope I didn't have to use W10, dang...) so I end up doing  option number 3... not ideal.

So i figured out that now that 18.04 is coming up, I would try to install ubuntu and THEN W10... I have read that that should keep W10 from overriding the bootloader (if not, then my question doesn't make any sense and I will try something else).
So more precisely I would like to know:
-first, will this stop W10 from overriding grub?
-should I install ubuntu (ubuntu-mate in fact) in UEFI mode?
-would it suffice to leave an empty space, format it to NTFS and let W10 do the rest during the installation process?

I have different computers and I will most likely upgrade them all... all HPs, with fairly "normal" hardware. In general terms, ubuntu (nor any other distro I've tried) has given me any problems for installing.

A possible solution for me would be to downgrade to W7, has never given me any problems... not a big fan of w10 anyway but I would like to stick with it as support will be an issue in a few years.

Not sure what other information would be needed for answering my question. Please let me know if you need any additional info.

Thanks in advance!!

Cheers,
Gonzalo

---

### Post by grahammechanical on 2018-03-23
I have no experience of Windows 10 and I do not have a UEFI motherboard but from the problems that people have reported on this forum over the years and from this Ubuntu wiki page

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I would say that If one OS is installed in UEFI mode then both OS must be installed in UEFI mode. 

Regards

---

### Post by yancek on 2018-03-23
The Ubuntu documentation on dual booting with windows in UEFI is at the link below and I would definitely suggest reading through it carefully.  If one is UEFI, then both should be UEFI for starters.
With windows 10, you should have an installation option of "Custom" which will allow you to select unallocated space or an ntfs formatted partition if one exists.
The windows EFI files will probably have priority, particularly if you are using HP as they violate the EFI standards.  You might read up on efibootmgr which you can use on Ubuntu or other Linux systems to modify the boot order for UEFI installs, among other things.

---

### Post by oldfred on 2018-03-23
With UEFI neither install overwrites the boot loader from the other. They share space in the ESP - efi system partition with separate folders.
But last system installed whether Linux, Windows or other will modify UEFI boot order to make it first to boot. Windows does not support booting Ubuntu so installing it last will still require boot order modification.

Windows 7 can be installed in UEFI boot mode, but DVD is BIOS only. You have to copy to flash drive and move files around to make it UEFI bootable.
UEFI only boots from /EFI/Boot/bootx64.efi on external devices or installers and that file actually then is unique to each installer.

With UEFI, Windows requires multiple partitions. Generally still best to install it first, but if unallocated space then you can install it second.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 

Windows in BIOS mode requires MBR partitioning.
Windows in UEFI mode requires gpt partitioning.

      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

