---
title: "USB3 disk install alongside Windows 10 (Acer Swirch 11)"
date: 2017-11-27
forum: Installation &amp; Upgrades
---

### Post by michfra on 2017-11-27
Hi forum,
I have made an USB disk from an olde laptop disk, and want to create a disk that contains Ubuntu.
So far I have installed files on the disk and asked for the boot loader to reside on the disk as well.
The purpose is to leave my Switch 11 intact, and boot normally when the USB disk is not attached.
When I attach this USB disk, I want it to boot Ubuntu directly by recognizing the boot loader installed on it.

So far I have failed in creating this setup.

My USB stick created by win32disk imager, boots fine and lets me start the installation, but after it finishes and I remove the usb stick installation media, my original windows boots again.

I have seen many posts about installing ubuntu alongside windows, but doing so by installing grub on the windows disk, and I want to try avoid this.

As I understand my Acer Switch, it has enabled secure boot and will only boot Windows. The usb sitck installation media does boot nicely however.

Is it not possible to create a bootable installation of Ubuntu with its grub loader on the same external usb drive?
Do I still somehow need to add a media in the windows boot loader?

I hope someone have tried the same installation type and is willing to share with me where I fail in this procedure.

Thanks
Michael

---

### Post by oldfred on 2017-11-27
I do create full UEFI bootable flash drives, and did with BIOS before. But you have to use one flash drive as installer and another as install location. Very difficult to use same flash drive. You use toram parameter, but if any issue you have destroyed installer with partial install and have to totally start over.

But with UEFI it is more complicated. Partially grub & partially UEFI.
Is this one of the systems with 32 bit UEFI but 64 bit?  If it boots Ubuntu directly it must be 64 bit UEFI as 32 bit requires another UEFI file.

UEFI only boots an external drive from /EFI/Boot/bootx64.efi. All installers, whether Windows or Linux use that file name, obviously different files.
And Ubuntu's grub only installs to ESP on internal drive into /EFI/ubuntu. If correctly installed you should be able to boot an install on a flash drive from that internal entry. But if an Acer need to set "trust".

But better to partition flash drive in advance, include an ESP - efi system partition (FAT32 with boot flag) on external & copy /EFI/ubuntu twice to flash drive's ESP. Once to /EFI/Boot and rename shimx64.efi to bootx64.efi. The version of grub/shim is internally coded to find more files in /EFI/ubuntu so both copies required.

       Acer Swift 3 Setting trust
[https://ubuntuforums.org/showthread.php?t=2370998](https://ubuntuforums.org/showthread.php?t=2370998)
Acer Aspire R3-131T-C770
[https://ubuntuforums.org/showthread.php?t=2365805](https://ubuntuforums.org/showthread.php?t=2365805)

---

### Post by ubfan1 on 2017-11-27
You're seeing the UEFI problem with a USB installation.  Take a look at bug 1173457 and add yourself.  The fix is a little manual fiddling -- ensure your USB got an EFI partition created (300M FAT32), copy the internal disk's EFI to the USB (the Windows stuff fits too), set your boot order to be the USB first, and that should boot.  In a bit of a hurry here,so might have left out something, but search this site and askubuntu, there are lots of problems like this for USB installtaion.

---

