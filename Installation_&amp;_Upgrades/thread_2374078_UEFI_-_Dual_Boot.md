---
title: "UEFI - Dual Boot"
date: 2017-10-12
forum: Installation &amp; Upgrades
---

### Post by Geoff_Lane on 2017-10-12
Folks,

Been running 16:04 for ages from an external USB stick but want to install to HD now.

My Toshiba Satellite has Windows 10 with EUFI - now I've not installed using EUFI before so am wondering, will it still install GRUB and if so where does it get installed?

The old BIOS was so easy but I don't want to mess up my Win10 installation though why not, I never use it.

Geffers

---

### Post by oldfred on 2017-10-12
Corrected title, its UEFI.
See very bottom of link in my signature for definitions of many Acronyms.

With UEFI all boot loaders for all systems are installed in the ESP - efi system partition. That is the FAT32 formatted partition.
If Windows already installed grub will add another folder in the ESP /EFI/ubuntu.

Even if you use Something Else, grub will always install to the ESP on sda, or if newer NVMe drive first one.

You have to boot the installer in UEFI mode to install in UEFI boot mode.
UEFI boot menu for flash drive should have two boot options, one UEFI:flash and the other as BIOS boot just "flash", where flash is the name or label of the flash drive.

You may have to turn off secure boot, turn on allow boot from USB ports, and turn off UEFI fast boot.
Also in Windows turn off Windows fast start up which is just hibernation. Linux NTFS driver will not mount hibernated NTFS, so then Linux cannot see the Windows install.

If you understand partitioning, often better to partition in advance with gparted & then use Something Else install option. While auto install usually works, I prefer to manage it myself.

---

### Post by Geoff_Lane on 2017-10-12
> **oldfred said:**
> Corrected title, its UEFI.
See very bottom of link in my signature for definitions of many Acronyms.

With UEFI all boot loaders for all systems are installed in the ESP - efi system partition. That is the FAT32 formatted partition.
If Windows already installed grub will add another folder in the ESP /EFI/ubuntu.

Even if you use Something Else, grub will always install to the ESP on sda, or if newer NVMe drive first one.

You have to boot the installer in UEFI mode to install in UEFI boot mode.
UEFI boot menu for flash drive should have two boot options, one UEFI:flash and the other as BIOS boot just "flash", where flash is the name or label of the flash drive.

You may have to turn off secure boot, turn on allow boot from USB ports, and turn off UEFI fast boot.
Also in Windows turn off Windows fast start up which is just hibernation. Linux NTFS driver will not mount hibernated NTFS, so then Linux cannot see the Windows install.

If you understand partitioning, often better to partition in advance with gparted & then use Something Else install option. While auto install usually works, I prefer to manage it myself.

Typed it correctly in subject field, why I typed in wrong in message no idea.

Understand partitions OK, used to play about with multiple boot partitions with the old original grub. Was aware that GRUB could be installed to the Disk Boot Sector or the Partition Boot Sector.

So, if I install under UEFI then at boot time do I get a menu as to which OS to boot?

Geffers

---

### Post by ubfan1 on 2017-10-12
Yes, grub menu should offer Windows as well as Ubuntu.  However, if secure boot is on, Windows may not actually boot through grub, you'd have to use the EFI menu, some function key at power-up to select boot device or OS.

---

### Post by oldfred on 2017-10-12
With gpt partitioning there still is a protective MBR. That is for old partition tools and it has one entry showing drive is all gpt, so old tool does not think it is blank.
And you then can (but not recommended) install BIOS boot grub to that protective MBR if on gpt you also have a bios_grub partition. 
On my old BIOS system I converted to gpt (also for future use if drive moved to a newer UEFI system) and had to use protective MBR.  

If system is UEFI and Windows is UEFI install, best to only have all drives as gpt and all installs as UEFI.

---

