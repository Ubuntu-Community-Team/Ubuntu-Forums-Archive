---
title: "Boot options?"
date: 2018-11-06
forum: Installation &amp; Upgrades
---

### Post by bob-2 on 2018-11-06
I have an Acer Spin315 I am trying to upgrade from Windows 10 to Ubuntu. But I cannot get the thing to boot from anything other than the hard disk. I quit using CD/DVD long ago. The EFI boot list has the USB devices listed first but the specific USB disk doesn't show up as bootable. I used DiskPart to create a FAT32 partition for the ISO and an EFI partition. Does the EFI have to be the first thing on the disk? If so, any thoughts how to make that happen? Thanks.

---

### Post by oldfred on 2018-11-06
How are you making flash drive installer?
You do not copy ISO to flash drive (normally).

       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[URL="https://help.ubuntu.com/community/Installation/iso2usb"]https://help.ubuntu.com/community/Installation/iso2usb
      [/URL]
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    
       Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) 
    
Note that with Acer once you have installer you have to from UEFI enable "trust" of the Ubuntu/grub .efi boot file(s).
       Acer Spin 5 Ubuntu 17.04 Needs Acer password & trust
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238) 
            Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    

[URL="https://help.ubuntu.com/community/Installation/iso2usb"]
[/URL]

---

