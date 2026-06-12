---
title: "Install 14.04 on a SSD disk with RAID 5 for storage and another ssd for cache"
date: 2016-08-13
forum: Installation &amp; Upgrades
---

### Post by huanfu1029 on 2016-08-13
Hi guys, 

I would like to install ubuntu 14.04 on a 256GB SSD , then use 3-3TB HDD's in a RAID5 configuration for file storage with SSD cache. 
How can I do this?

1. Samsung 850 EVO 250GB 2.5in SATA III Internal SSD  (for OS)
2. Western Digital RE 3TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" (3 for RAID5)
3.SSD M.2 SATA MODULE SAMSUNG XP941 M.2 512GB PCI EXPRESS  (for cache)

much thx and best regards

---

### Post by oldfred on 2016-08-14
I do not know RAID and I can move thread to server sub-forum where those that know RAID may be able to help.

But I believe install to SSD is just like any install, and then you configure RAID drives.
Your 3TB drives will have to use gpt partitioning.

But SSD can be MBR or gpt, but if only Ubuntu better to be gpt. And then you have to decide if UEFI or BIOS. If hardware is UEFI probably better to use UEFI.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

I use gpt, but not RAID. You can partition with gdisk, parted or gparted if installing with live installer, not server version as it has no live system nor gui.

       
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

      [/URL]
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 
In parted it is the mklabel command where choice can be gpt or msdos amoung others. 
See man parted.

This is now older, but not sure a server RAID install is much different. Are you installing FakeRAID (BIOS) or software RAID, or do you have proprietary RAID card? All different.
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

    [URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

