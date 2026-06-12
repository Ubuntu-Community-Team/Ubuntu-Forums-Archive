---
title: "Grub will link to Ubuntu 16.04 but show Win10 together"
date: 2016-05-24
forum: Installation &amp; Upgrades
---

### Post by gwill83419 on 2016-05-24
I'm sure I'm doing something silly but not sure what. I'd like Grub to show both Ubuntu 16.04 or Win 10.
Any guidance appreciated.

Link:
[http://paste.ubuntu.com/16661839/](http://paste.ubuntu.com/16661839/)

Thanks
Graham.

---

### Post by grahammechanical on 2016-05-24
> =================== Blockers in case of suggested repair The boot of your PC is in Legacy mode. Please change it to EFI mode. 
Please use Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")) which contains an EFI-compatible version of this software. ((use it from live-USB, not from DVD))


Windows 8 is installed in efi mode. Look at sda1. It has Windows efi boot files. But there are no Ubuntu efi boot files. Ubuntu is installed in BIOS/Legacy/CSM mode. That is the cause of this situation. And I do not think that boot repair can repair it because you are using Boot Repair on a 32 bit OS. Did you download the 32 bit version of Ubuntu. i386 ISO image? Did you install the i386 version of Ubuntu or the amd64 version?

> **Case when Ubuntu must be installed in UEFI mode**
Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]


> **General principles**
To install Ubuntu in UEFI mode: 


[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 
[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 
[*]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode. 
[*]Use  a supported version of Ubuntu. Support for UEFI appeared in 11.10, but  has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2. 
[*]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in UEFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below) 
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by gwill83419 on 2016-05-25
Thanks for your reply.
As far as I know I used the latest 64bit Boot repair ( Latest one with the Green background and the Very happy person).
Likewise I installed the 64 Bit version of Ubuntu 16.04.
I thought it strange when looking at the terminal as Boot Repair downloaded files that it mentioned i386. Hmm.
Anyway It looks as if I should: 
Reset all Bios setting other than the changes you mention above.
Backup and reinstall 64bit Ubuntu.16.04.
Can you tell me. Do all versions of 64bit Ubuntu 16.04 support UEFI, I don't have to look for a special version?

Graham

---

### Post by gwill83419 on 2016-05-25
Ok I've read all the links and answered my final question above.
Secure Boot: The computer has pre installed Win 10. Do I need to add Secure boot to Ubuntu 16.04 LTS 64bit? will I be able to dual boot without it?

Graham.

---

### Post by oldfred on 2016-05-25
How you boot install media is how it installs.
New UEFI systems have three boot modes, UEFI with Secure Boot, UEFI and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

You separately choose how you boot flash drive. Some systems will not even let you boot flash drive with Secure boot on, and/or need a USB/flash drive setting changed to allow boot of flash drive. My desktop also has settings on USB boot for UEFI only, UEFI and CSM. I could only get flash drive to boot in UEFI mode with UEFI only boot mode, even though flash drive Ubuntu 64 bit installer is configured for both BIOS & UEFI boot.
But then how you install, may not match default boot mode in UEFI. So you have to check that matches.

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

If install is on a gpt partitioned drive & you have an existing ESP - efi system partition, Boot-Repair's advanced mode has options to uninstall/reinstall grub. Be sure to boot in UEFI boot mode.
It really is just un-installing grub-pc(BIOS) and installing grub-efi-amd64(UEFI) which also changes a few other settings.

---

### Post by gwill83419 on 2016-05-26
Thanks oldfred.

---

