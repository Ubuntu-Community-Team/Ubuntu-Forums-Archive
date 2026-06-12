---
title: "Trying to dual boot 12.04 with Win 7; Win 7 not detected during installation"
date: 2014-05-16
forum: Installation &amp; Upgrades
---

### Post by mreasy2 on 2014-05-16
Hey there,  I'm trying to dual boot my Asus K55A laptop with Win 7 and Ubuntu 12.04.  The system came preloaded with Win8, and I just this past week had enough and did a clean install of Win 7.  Now, I'm pretty sure it was a UEFI set up with Win 8, but I had to enable CSM in the BIOS to install Win 7.  It's not on an EFI partition, I know that for sure. I made a bootable usb drive with the Ubuntu 12.04 image and it seems to work just fine.  However, when I try to install Ubuntu it doesn't actually recognize the existence of any other operating system.  I'm pretty sure this is because the flash drive is not booting in Legacy BIOS mode.  When I jumped into my bios and checked the boot order it was listed as UEFI.    So, I guess my question is, is there a way I can get my system to boot the Ubuntu flash drive in legacy bios mode, or a way to work around the problem I'm having?  I am, obviously, a complete Linux noob, but I really want to give it a shot.

---

### Post by oldfred on 2014-05-17
The issue is your conversion from gpt required for UEFI to MBR required to BIOS. Windows does not correctly convert drive and leaves backup gpt partition on drive. Linux tools see MBR & backup gpt and do not know what you want.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You can also convert a Windows 7 DVD installer that is BIOS only to UEFI by copying to flash drive and doing some updates.

 Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

This was an UEFI install, but you may have some of the same issues.

 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

---

### Post by mreasy2 on 2014-05-17
Huh.  Thanks for the reply.  Unfortunately, I'm still a bit confused--going to keep trying, though.    To be clear, Win7 is already installed an is definitely not on a UEFI partition.  My flash drive with Ubuntu is UEFI.  I know they both have to be the same (UEFI or Legacy, not both).  Since Win7 is already installed without UEFI, I was trying to do the same with Ubuntu but I can't figure out how to make the flash drive non-UEFI.  Unless I missed something, most of the links you shared seem to be the other way around: trying to force something to boot as UEFI.    Like I said, gonna keep at it.  Thanks again.

---

### Post by oldfred on 2014-05-17
When you converted drive with Windows BIOS installer it left gpt data on drive. You have to remove that first.

The Ubuntu installer is both UEFI & BIOS. In your UEFI/BIOS menu you should have two entries for flash drive - one UEFI and the other is BIOS, but often not clearly stating that.

---

