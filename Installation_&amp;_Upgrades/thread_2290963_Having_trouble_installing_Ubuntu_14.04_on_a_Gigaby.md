---
title: "Having trouble installing Ubuntu 14.04 on a Gigabyte A88X MB"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by tvsraman on 2015-08-16
I have the following system under development:
MB: Gigabyte GA-F2A88XM-D3H
RAM: DDR3, ADATA, 1600, 16 Gb (4x4Gb)
HDD: WD 500 Gb
DVD: ASUS
BIOS: AMI UEFI
BIOS version: F8, it was F7 which I have upgraded to F8 with Gigabyte BIOS utility QFlash
I am able to do partitions but I am unable to load Ubuntu 14.04 fully. It loads the OS partially and then I get the error that unable to load further modules of the OS. I also tweaked the BIOS bu enabling AMD Memory Profile (AMP) and enabling "Native IDE" under SATA support, rest of the BIOS left as default. I tried loading the Ubuntu several times but with the same result after loading about 11%.
When I Googled this problem for this MB I got a few postings indicating that this MB is exclusively designed for Windows 8 and above. Before I invest in Windows 8.1, I would like to know whether Ubuntu can be successfully loaded on to HDD with this MB. I have also posted similar query with Gigabyte Support as to the exclusivity of their MB for Windows.
I would very much appreciate any help.
Sivaraman.

---

### Post by oldfred on 2015-08-17
Some with Gigabyte have installed.
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

But are you installing in UEFI mode or BIOS boot mode?
Generally better in UEFI mode, but then should not have drives in IDE mode but AHCI.

I installed to an Asus Z97 and had to change a lot of UEFI settings. While we say to turn off secure boot, some of these systems just say Windows boot mode. That seems to mean Windows secure boot. So I changed to "Other" but then had issues getting it to boot in UEFI mode not CSM/BIOS mode. But every brand has different settings.

---

### Post by tvsraman on 2015-08-17
I am sorry I forgot to mention the processor, I am using AMD A8-7600 (Kaveri core) and only F7 version of BIOS supports this processor.
I am using UEFI and Legacy mode under "Boot Mode Selection". I have not yet tried by enabling IOMMU. 
Thanks for the links, I will certainly look into it.

---

