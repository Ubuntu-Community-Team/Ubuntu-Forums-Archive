---
title: "manual partitioning with RAID, LUKS, LVM and UEFI"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by aofansome on 2012-08-13
I'm installing Ubuntu 12.04 x64 desktop on my first UEFI machine (Gateway DX4860).  I'm using the alternate install CD, with manual partitioning.  I want /boot on a micro SD card, and everything else on a RAID5 array (Linux) with LUKS encryption and LVM.

If I install using the non-UEFI optical drive boot menu entry, and create a standard Ext4 /boot partition on the micro SD card, everything works as expected.  But I don't understand how to partition manually to get what I want with UEFI.  I've searched here and googled, but haven't found enough to get me there.  Please point me to instructions or other resources.

If I install using the UEFI optical drive boot menu entry, and automatically partition the micro SD card, I get a working UEFI system (with the other disks disconnected).

---

### Post by oldfred on 2012-08-13
I do not think I have seen anyone with a separate /boot and UEFI, but I do not see why not. 

But is efi partition on Internal hard drive or SD card. Normal UEFI has to have efi as first partition for UEFI to boot. If you can set UEFI/BIOS to boot from SD card then I would think you need both efi and /boot partitions on the SD card. Grub-efi then is installed to the efi partition and system boots to efi, then /boot and then system? Location on drives should not matter as long as they are all there and specified as part of system.

I think SD card also has to be gpt partitions for efi to work. I have gpt partitions on a USB flash with a bios_grub partition as I still have BIOS, but once set up it worked just like the old MBR(msdos) partitions.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

I do not think any of these links discuss your configuration, but do help explain UEFI, gpt & grub2.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.Must be 64bit version to have UEFI

---

### Post by aofansome on 2012-08-13
Thank you, oldfred. I'll read the resources that you provided, and redo installs using manual partitioning.

Update: Manual partitioning works fine if I create both EFI system and boot partitions on the SD card. I know that it's UEFI booting because I see /sys/firmware/efi/vars/*. Thanks again.

---

