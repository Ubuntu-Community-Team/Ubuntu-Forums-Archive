---
title: "Install Ubuntu in UEFI in three simple steps"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by PeterTaps on 2014-12-22
I am used to installing dual boot under legacy BIOS but had problems doing so on UEFI bios. During boot, I would always have to press boot menu key to select Ubuntu. If I don't do so, it will quickly boot into Windows.

I finally managed to install Windows and Ubuntu 14.01 dual boot under UEFI. Just wanted to share my steps. 

On the computer, I first installed Windows 8.1 in a partition. I keep Windows around for updating bios, etc. Now, to install Ubuntu, follow these steps:

1. Make sure BIOS supports UEFI.
2. Put the Ubutu OS CD in. When booting the computer, press proper key to get the boot menu (for my Gigabyte motherboard, the key is F12) and select "Boot from CD as UEFI."
3. During the install, when you have to mount "/" on a partition, don't mark that partition as bootable. Install will automatically detect and update EFI sector.

This is all I had to do. When I reboot the machine, now I get the familiar boot menu that lets me choose between Ubuntu and Windows, the default being Ubuntu.

For experts on this forum, would appreciate your feedback.

Regards,
Peter

---

### Post by birkopf on 2014-12-22
If this worked for you - you are really lucky :) 

Most of us have real problem with EFI. In general - I would not recommend installing GRUB in MBR (that is in /) 
It should be normally installed in EFI partition which usually is sda2.

---

### Post by oldfred on 2014-12-22
When installing in UEFI mode the installer seems to be smart enough that whether you specify drive like sda or partition like sda2, it will install the efi files to the correct efi partition. But drive must be gpt partitioned and have boot flag on the FAT32 partition that is then seen as the efi partition.

If in BIOS mode grub should only be installed to MBR or drive like sda.

You mentioned Gigabyte, many other users with Gigabyte motherboards needed IOMMU setting changed in UEFI/BIOS.
 Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

---

