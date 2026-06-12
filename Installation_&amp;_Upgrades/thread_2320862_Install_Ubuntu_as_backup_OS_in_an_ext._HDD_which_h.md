---
title: "Install Ubuntu as backup OS in an ext. HDD which has 1 more partition"
date: 2016-04-18
forum: Installation &amp; Upgrades
---

### Post by tanersirakorn on 2016-04-18
Hello, this is quite complicated for me.

I have a 2TB WD Passport External HDD, which I planned to split it up to 4 partitions. Three are going to be FAT32 filesystems for storing files, and another one ext filesystem, which I planned to install Ubuntu (to be used when I am on public computers and to be used when my primary computer drive was screwed), and some 20GB unallocated memory left (which I don't know why I love to do this).

So, I was confused by this – can I just boot the Live USB and install Ubuntu on the ext partition? Are there any concerns about the hard drive structure I should be know? And how about the GRUB, just choose to install it at my ext. HDD right?

Thanks for helping, I've really forgotten almost everything about linux (except don't rm -rf /)!

---

### Post by sudodus on 2016-04-18
Welcome to the Ubuntu Forums :-)

A few years ago, yes. But now there is UEFI in addition to the classical BIOS boot system. In BIOS, a standard installed system will work well (and is portable, if you avoid proprietary drivers for graphics and wifi) in computers running in BIOS mode. But if you install in UEFI mode, a standard installed system will work well (is not portable).

I made some systems, that are portable between UEFI and BIOS mode,

1. Persistent live system, see this link: [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

2. Portable installed system (for cases like yours), see this link: [Portable installed system booting from UEFI & BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

I suggest that you try both systems and settle with the system you prefer. It is probably easier to start from the compressed image files, that I have uploaded, but there should be instructions enogh for you to create your own custom made system.

The compressed image files will overwrite the target drive, so you must copy all important files from your 2 TB drive to a safe place before using the compressed image files. You need an extra ***backup*** in any case because installing an operating system is risky.

***Edit:*** At least until recently, Windows will only read the first partition (logical number one), which is prepared in the persistent live system. Partition #1 is an NTFS partition, that can be used to transfer files between running Windows systems and linux systems (including the system on the drive). I think it is more flexible in drives with a GUID partition table (GPT).

---

### Post by oldfred on 2016-04-18
FAT32 is ok for smaller partitions, but NTFS has journal and can store a file over 4GB where FAT32 cannot.

Windows XP which no one should be using was the only version that could not read & write from gpt partitioned drives.
A 2TiB drive is the maximum for MBR partitioning which also has a 4 primary partition limit. But Ubuntu will boot from logical partitions without issue. It just is that one primary must be the extended to act as a container for all the logicals. One advantage of gpt over MBR.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

