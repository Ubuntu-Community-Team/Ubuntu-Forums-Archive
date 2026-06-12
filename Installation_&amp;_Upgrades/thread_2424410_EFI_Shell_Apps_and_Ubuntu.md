---
title: "EFI Shell Apps and Ubuntu"
date: 2019-08-08
forum: Installation &amp; Upgrades
---

### Post by namalik on 2019-08-08
Hi,

I am running Ubuntu on a GPT/ UEFI based USB and wondering if I can launch an EFI Shell Application (BootX64.efi) within Ubuntu?

I know I can launch such application via a separate USB stick by formatting the USB stick with FAT32 on GPT layout, but wondering if I can run / launch the EFI application directly from Ubuntu.

---

### Post by oldfred on 2019-08-08
No, but some commands like efibootmgr are in Ubuntu. You have to boot to get to bootx64.efi.
see
man efibootmgr

Grub replaces bootx64.efi with a copy of grub on internal drive. Windows normally also does same thing. On internal drives bootx64.efi is the fallback or hard drive boot entry.
The bootx64.efi is the default UEFI boot for external drives.

[https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)
       [https://software.intel.com/en-us/articles/efi-shells-and-scripting](https://software.intel.com/en-us/articles/efi-shells-and-scripting)

---

### Post by namalik on 2019-08-08
Hi and thanks for reply.

Assuming I have Ubuntu on a USB Stick, can I create a FAT32 partition and make a sort of dual-boot USB? When I create a new partition and but shell app, then Ubuntu installation was compromised (I was able to boot either from FAT parition or from ubuntu if delete the EFI parition.

---

### Post by oldfred on 2019-08-08
Standard installer can be configured multiple ways. Most now use dd to create a hybrid DVD/flash drive which does not have partitions. But you can just copy all the files to a FAT32 formated flash drive with boot flag.

       UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

But only one FAT32 formatted partition can have boot flag or be the ESP - efi system partition per device.
 
Or you can do a full install to flash drive, if drive is a bit larger. I have full installs on most of my flash drives that are 16GB or more, even if for data backup. But just for emergency boot.  I also now use my old obsolete tiny flash drives like 1 or 2GB as emergency boot using rEFInd.

I have not found I need shell or shell commands. The efibootmgr and ways to boot Ubuntu or emergency boot are all I have needed.

---

