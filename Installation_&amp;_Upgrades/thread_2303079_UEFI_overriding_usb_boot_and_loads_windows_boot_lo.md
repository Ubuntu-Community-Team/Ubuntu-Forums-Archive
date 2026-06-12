---
title: "UEFI overriding usb boot and loads windows boot loader."
date: 2015-11-16
forum: Installation &amp; Upgrades
---

### Post by sms28 on 2015-11-16
Hi guys, I'm very much new to linux and would love to experience the OS. I have a fairly new HP 15-AC 047TU lapptop, with Windows 8.1 pre-installed. It's a UEFI board with Legacy support. I want to dual boot the 8.1 and Ubuntu, and in a near future upgrade the 8.1 to Windows 10. I've been trying to install Ubuntu 14.04LTS. I've downloaded the iso image, burned into usb. I enabled Legacy support, disabled secure boot and made usb diskette top priority at boot order under boot options. Still the firmware somehow overrides the boot order completely and loads Windows 8.1. I've read somewhere to disable the 'fast boot' option in 'what power button do' sub-option in Power Options, Control Panel; but my laptop doesn't have that particular option. Please Help! Thanks in advance.

---

### Post by grahammechanical on 2015-11-16
> In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").

So, in the BIOS/UEFI and in Windows itself

You do need to comply with the advice given in this wiki page. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
> 
**Case when Ubuntu must be installed in UEFI mode**

 Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]


I am assured that Windows 8.1 is always installed in EFI mode when it comes pre-installed. And you have installed Ubuntu in legacy mode. That most definitely causes problems. We have had many posts about that situation.

You will also find many posts on this forum of people upgrading Windows 8.1 to Windows 10 and loosing Ubuntu in process. If you fix this Ubuntu install then it will be broken when you upgrade to Windows 10. I would suggest that it is better to upgrade to Windows 10 and to then install Ubuntu and this time install Ubuntu in EFI mode.

Regards.

---

### Post by oldfred on 2015-11-16
If you install Ubuntu in Legacy/CSM/BIOS boot mode you have to go into UEFI and turn off UEFI and/or turn on CSM/Legacy to boot in BIOS mode. It is set to boot in UEFI mode.

And HP is not particularly friendly with UEFI boot of anything other than Windows. It violates UEFI standard and also uses description as part of boot and only valid description is "Windows".
But there are many work arounds, most copy Ubuntu's efi boot files into /EFI/Boot and rename shimx64.efi to bootx64.efi.
The bootx64.efi is a fallback or hard drive boot entry. It is used to boot a device. And is the file used by Windows on a Windows UEFI bootable flash drive and on Ubuntu's UEFI flash drive installer.

You can use Boot-Repair to convert a BIOS/CSM install to UEFI. It really just un-installs grub-pc(BIOS) and installs grub-efi-amd64(UEFI) with some internal settings changes that grub handles. Actual install is the same.
       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

    
       HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

[URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL]

---

