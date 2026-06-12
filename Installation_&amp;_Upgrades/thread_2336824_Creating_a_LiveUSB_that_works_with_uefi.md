---
title: "Creating a LiveUSB that works with uefi"
date: 2016-09-11
forum: Installation &amp; Upgrades
---

### Post by sideburns on 2016-09-11
I'm trying to help a friend experiment with Linux, but her computer refuses to boot from my USB because it's not UEFI.  What do I need to do?

---

### Post by oldfred on 2016-09-11
Standard Ubuntu live installer is both UEFI & BIOS by default. But you have to correctly choose to boot in UEFI mode from UEFI. Usually will show two boot options for a flash drive: UEFI:Flash and Flash (BIOS). If UEFI Secure Boot is on, you may have to allow boot from flash drive or turn on USB ports. Often easier to turn Secure boot off.

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

      
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by sideburns on 2016-09-11
OK, so it's probably an issue with the laptop's boot manager or BIOS setup screens.  Will try again later, and mark this solved if that works.  Also, as my .sig notes, I don't use Ubuntu myself, but I do know how to make a LiveUSB under Fedora, using unetbootin.  Still, pointing to the Ubuntu instructions may well help somebody else.  Thanx for your quick reply.

---

