---
title: "Grub turn off efi mode"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by c-m on 2014-05-08
How do I prevent grub from installing the efi version?

I have booted from a live USB created using Netbootin on OSX and installed Ubuntu onto a USB hard drive with MBR partition table (not GPT), yet for some reason the installation always sets grub up as EFI. I don't even have an EFI partition. I have even ran boot repair, and all it does when I try to install grub to /dev/sdb is say "why don't you try creating an EFI parition?" It fails to install the standard non-efi grub.

---

### Post by grahammechanical on 2014-05-08
I wonder if you are confusing GPT and UEFI.

> [COLOR=#252525][FONT=sans-serif]UEFI is meant to replace the Basic Input/Output System ([/FONT][/COLOR][BIOS]("http://en.wikipedia.org/wiki/BIOS")[COLOR=#252525][FONT=sans-serif]) firmware [/FONT][/COLOR]

> [COLOR=#252525][FONT=sans-serif]Although it forms a part of the [/FONT][/COLOR][Unified Extensible Firmware Interface]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface")[COLOR=#252525][FONT=sans-serif] (UEFI) standard ([/FONT][/COLOR][Unified EFI Forum]("http://en.wikipedia.org/wiki/Unified_EFI_Forum")[COLOR=#252525][FONT=sans-serif] proposed replacement for the [/FONT][/COLOR][PC]("http://en.wikipedia.org/wiki/IBM_PC")[BIOS]("http://en.wikipedia.org/wiki/BIOS")[COLOR=#252525][FONT=sans-serif]), it is also used on some BIOS systems because of the limitations of [/FONT][/COLOR][master boot record]("http://en.wikipedia.org/wiki/Master_boot_record")[COLOR=#252525][FONT=sans-serif] (MBR) partition tables,[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

If your motherboard has a EFI/UEFI boot system then I do not think that you will be able to stop Grub setting up as EFI. Unless you set Legacy mode. 

> 
[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[/LIST]

> [COLOR=#333333][FONT=Ubuntu]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu]Remark: Some BIOSes allow one to set up the boot mode for the optical drive separately from the boot mode for the HDD.[/FONT][/COLOR]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Regards.

---

### Post by c-m on 2014-05-08
Nope not confusing anything I'm afraid.

My motherboard will boot both UEFI and bios mode. Stricktly speaking the motherboard only has a bios it doesn't have UEFI.

It's an Intel DG41AN which previously had a Ubuntu on in regular bios mode without any issue.

The problem is that when installed from a live usb booted in EFI mode because the live usb will not boot in bios mode, it installs Ubuntu with Grub in EFI mode. I do not want this. I want it to install Gurb in regular mode. 

The installation is to an external disk /dev/sdb3 (boot flag is on that partition). Gurb has been told to install to the MBR of /dev/sdb.

I've never had to do anything special before, but then my Live USBs were always created on an existing Ubuntu system using Netbootin and not via a Mac using Netbootin.

Cheers.

---

### Post by Luke M on 2014-05-08
The installer always installs in EFI mode if you boot it in EFI mode. So you need to boot it in BIOS mode.

If you don't know how to select between BIOS and EFI on your system, you could try renaming the "boot" directory on the USB stick. That would prevent EFI booting.

---

### Post by c-m on 2014-05-08
It's not a case of selecting either or in the bios, enabling EFI boot in the bios doesn't prevent regular boot. At least it never has in the four years I've owned this board. 

If I turn Enable EFI boot off in the bios then the live usb stick will not boot at all even if I delete/rename the /boot directory

---

### Post by ubfan1 on 2014-05-08
The Ubuntu live media should definitely boot either way, using the grub bootloader for UEFI and the syslinux bootloader for legacy boot.

---

