---
title: "Installing lts ubuntu from usb"
date: 2018-02-02
forum: Installation &amp; Upgrades
---

### Post by tech-gamer on 2018-02-02
Hi. I putted files inside ubuntu iso files into usb and booted from usb. But it went straight into grub. I did chainloader +1
And it said error: invalid EFI file path

---

### Post by oldfred on 2018-02-02
Is this an UEFI system? What brand/model?
Most use various installers to extract ISO, format flash drive and add boot loader. 
If just UEFI you can do that yourself, but have to directly boot from UEFI, not from another grub on hard drive.

       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 


 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)
[https://ubuntuforums.org/showthread.php?t=2299040](https://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by oldos2er on 2018-02-02
Did you "burn" the ISO to the USB flash drive? Simply copying it there won't work, nor will extracting the ISO and then copying.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Please provide some basic information about your hardware specs, any currently installed OSes, and whether your system uses UEFI or MBR.

---

### Post by TheFu on 2018-02-02
Great!  Is that what you wanted or is there some question?

Copying ISO files onto a USB is not sufficient to make it boot.  Perhaps if you explain exactly what you did, someone could help?
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu) might be helpful.

---

