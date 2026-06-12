---
title: "Ubuntu won't boot on UEFI mode install."
date: 2018-03-04
forum: Installation &amp; Upgrades
---

### Post by pchiossi on 2018-03-04
I was trying to solve an annoying problem that I have in my laptop: 

I installed Windows10 on UEFI mode and Ubuntu/linux on Legacy mode. It's a dual boot system but with two separate disks, a SSD and a HDD. Windows10 is installed on the SSD and Linux on the HDD. What I wanted to do was to reinstall Ubuntu on UEFI mode so I could successfully boot on any OS using GRUB, because lately I had to get into my BIOS settings and change the boot in order to access the OS I wanted, since grub was not recognizing Windows on UEFI mode. 

Anyway, I tried reintalling Ubuntu by formating the old installation and manually adding an EFI partition using GParted, I did everything following the instructions on  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) . After I installed it, I did a reboot, set the BIOS to boot on the EFI partition, and nothing, doesn't boot. So I did, the Boot-repair thing on the Live-USB, and still doesn't boot. 

This is the paste URL from Boot-Repair: [http://paste.ubuntu.com/p/gddyyWRY9k/](http://paste.ubuntu.com/p/gddyyWRY9k/)

Can someone help me? Does GRUB works on two separate disks? Is that the problem? I'm clueless here.

---

### Post by oldfred on 2018-03-04
While the Ubuntu live installer is really a MBR drive for greater compatibility and then able to boot in UEFI or BIOS boot mode, standard UEFI should normally use gpt partitioning.
Windows requires gpt partitioning for UEFI boot.
But your sda drive is MBR(msdos) partitioned. And you have the ESP in a logical partition. It seems the installer installed that ok, but your system may or may not like that configuration for UEFI boot.

I really suggest backing up anything on sda and converting to gpt. 
And generally the ESP - efi system partition is one of the first couple of partitions.

You may be able to convert, but still must have backups.
       Converting to or from GPT
[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]http://www.rodsbooks.com/gdisk/mbr2gpt.html

      [/URL]
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 
    [URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]
[/URL]

---

