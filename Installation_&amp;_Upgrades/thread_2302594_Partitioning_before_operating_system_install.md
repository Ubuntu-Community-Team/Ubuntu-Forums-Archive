---
title: "Partitioning before operating system install"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by jrh74 on 2015-11-11
I would like to install windows 7, windows 10 and ubuntu 14.04 on my1000  Gb disk in three separate partitions of approximately 330 Gb each.   After installing windows 7, I tried to reduce the size of the partition  it was on to 330 Gb but was only allowed to shrink to 469.38 (about 50  percent).  From reading the windows 7 "disk management help", it seems this is  caused by unmovable files?   the instructions for solving this problem  while in windows 7 seems very complicated (out of my league). Is there a  way to partition the drive before installing any operating systems. If  so, how might this be done?  Note that I have no problem reinstalling windows 7 if that  will get me over this hump.  Note also, that partitions will have to be NTFS (at least for windows). 

Processor: Intel core i5-3750k 3rd Gen unlocked @3.40 GHz
Mother board: ASRock Z77 Pro 4
Operating system: See above.
Hard Drive: WDOEM  WD1TB BLUE SATA6.0 HD (1000 Gb)
SECOND Hard Drive: Toshiba (500 GB)
Memory: CRUCIAL 8GB 4X2D3 1333 DIMM CL
TV tuner: Hauppauge WinTV-HVR-2250

---

### Post by grahammechanical on 2015-11-11
From following threads on this forum I have recognised a few simple rules

1) Use Windows utilities to defrag Windows more than once and restart windows each time before resizing Windows partitions.
2) Use Windows utilities to resize/move/create Windows partitions and to create unallocated space.
3) Use Linux/Ubuntu utilities to convert unallocated space into Linux partitions to be used by Ubuntu.

I cannot give any advice as to the number of partitions that any version of Windows requires. It certainly is possible to delete and create a new partition table from a Ubuntu Live session using Gparted. The partition table should be GPT as I believe that Windows 10 requires GPT. Although I will not swear to it.

From there it should be possible to create partitions and have them formatted. How useful Windows utilities are at doing this I cannot say. Gparted will do it. I also think that a Windows install disk will work better if it is used to format any partition for use with Windows.

I also suspect that Windows 10 will need a boot partition. How much control Windows installer gives I cannot say. But the Ubuntu installer will give you control if you choose the Something Else option. Ubuntu needs 2 partitions, one for Ubuntu and one for swap. We can have others but that is the minimum.

If the motherboard has a UEFI boot system then the situation becomes slightly more complicated.

Regards.

---

### Post by ubfan1 on 2015-11-11
The Windows pagefile is probably the one which is considered "immovable", so in your performance settings, just delete it before defragging. Then the shrink should work better.

---

### Post by oldfred on 2015-11-11
You have newer hardware that is UEFI.
But Windows 7 DVD default installs in BIOS boot mode. You can convert to UEFI installer by copying to a flash drive and moving some files around.
        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

How you boot installer is how it installs for both Ubuntu & Windows. If you want all 3 in BIOS mode then you can install that way. But once drive is MBR partitioned, Windows can only be BIOS boot.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

   UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

