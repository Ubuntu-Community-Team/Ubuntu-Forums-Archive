---
title: "Dual boot install - Win7+Ubuntu 12.04 - Ubuntu installer sees no partitions"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by wb0gaz on 2013-02-20
I am installing dual boot OS (Windows 7 + Ubuntu 12.04) on HP Pavilion G6 laptop (AMD CPU). The machine was shipped with Windows 8 which I backed up then deleted all partitions before proceeding (I don't want to use Windows 8.)

The first OS is a fresh install of Windows 7, using part of the hard drive space (manually created the C drive partition during the Windows 7 isntall process, left remaining space for Ubuntu). I then rebooted with Ubuntu 12.04 Alternate install CD, and when it arrived at partition configuration step, Ubuntu did not see any partitions (shows the whole drive as empty.) As I didn't want to destroy the Windows 7 installation, I didn't proceed.

The laptop has EFI BIOS which I've set to legacy compatible, with secure boot disabled. I've never run into this (empty partition table seen when adding Linux to existing Windows system), and have otherwise built a number of dual-boot configurations without difficulty, but this is my first attempt with EFI BIOS, so I may be overlooking important steps or considerations.

Any clues where to start on this?

Thanks very much

---

### Post by wb0gaz on 2013-02-21
Some additional information and concern -

I'm using the Ubuntu 12.04 Alternate (64-bit) installer CD to install Ubuntu as second OS alongside Windows 7 which itself was a fresh install onto the first partitions of the hard drive.

During the installation process, it is giving a warning of sorts about GPT (GUID partition table).

My concern is this - the Alternate installer is evidently detecting presence of GUID partition table (it issues a warning message that GPT exists), but Ubuntu installer does not use it, instead shows an (allegedly) empty drive.

It is clear that proceeding with the installation onto the (allegedly) empty hard drive will destroy the Windows 7 installation. I believe this is a problem --- the Alternate installer should offer option to use the GUID partition table, rather than the (somewhat cryptic) warning message and offer to install onto an empty partition table.

How do I tell Ubuntu Alternate installer to use GUID partition table to install Ubuntu alongside existing Windows 7 installation?

Thank you

---

### Post by oldfred on 2013-02-21
You can not unless you installed Windows 7 in UEFI mode.

Windows only boots from gpt partitioned drives with UEFI. And UEFI required gpt partitioning.
Ubuntu will boot from BIOS with either MBR or gpt partitioned drives. 

Also Windows installed in BIOS mode will convert a gpt drive to MBR, but gpt also has a backup gpt partition table. Windows only converts primary gpt table, so Linux tools see MBR and gpt backup and get confused.

If Windows is BIOS/MBR, you will have to install Ubuntu in MBR mode. And you are back to the issue of 4 primary partitions. With gpt you can only have 128 primary partitions. :)

To remove backup gpt table.
       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by wb0gaz on 2013-02-21
Thank you very much Oldfred, I appreciate the helpful detail!

---

