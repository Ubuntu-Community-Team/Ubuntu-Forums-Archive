---
title: "Failed installation prevents further attempts"
date: 2018-12-25
forum: Installation &amp; Upgrades
---

### Post by arcanechaos on 2018-12-25
[LEFT][COLOR=#242729][FONT=Arial][SIZE=3]I was in the process of installing Ubuntu 18.04 on my laptop when the screen timed out. Moving the mouse and using the keyboard would not bring back the screen, and after a couple hours I was forced to power cycle the laptop after I was unable to resume. [/SIZE][/FONT][/COLOR][/LEFT][SIZE=3][LEFT][COLOR=#242729][FONT=Arial][/FONT][/COLOR][/LEFT][/SIZE][LEFT][COLOR=#242729][FONT=Arial][SIZE=3]When I attempt to boot off the liveCD again to again attempt installation I get an error message that it is unable to find /BOOT/EFI/mmx64.efi and the laptop shuts off immediately afterwards; however I am able to boot to windows 10 with the DVD removed. After looking online for a solution and playing around with the EFI partition I have not progressed any further than I was before. Every solution I have found online assumes that either the user can boot Ubuntu or is able to boot off the liveCD, which I can do neither. Does anyone have any idea what the way ahead is to be able to install ubuntu?

I have also attempted to scrub the EFI partition to just leave Windows; however I still have a BBS priority option for Ubuntu. Is there somewhere else on the hard drive I need to look? I am assuming if I can remove all traces of the previous installation that I can just install off the liveCD like I tried to do originally.
[/SIZE][/FONT][/COLOR][/LEFT][SIZE=3][LEFT][COLOR=#242729][FONT=Arial][/FONT][/COLOR][/LEFT][/SIZE][LEFT][COLOR=#242729][FONT=Arial][SIZE=3]I am running a MSI GT72S, and I am attempting to dual-boot with Windows 10.[/SIZE][/FONT][/COLOR][/LEFT][SIZE=3][/SIZE]

---

### Post by oldfred on 2018-12-25
Some work arounds here:
 System fails to boot with \EFI\BOOT\mmx64.efi - Not Found
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171) 
Some just copy grubx64.efi into /EFI/Boot and rename it to mmx64.efi. but make sure Secure Boot is off.
It seems some tools to create the live installer, do not correctly configure /EFI/Boot.

The mmx64.efi in an install is the UEFI key manager for Secure boot on added files. If you have UEFI Secure boot on and want to install proprietary drivers, Canonical  cannot verify secure boot process, but a user can (but then assumes responsibility). Before you just had to have Secure boot off. 

    
Some other MSI installs & issues they had to resolve.
      
 MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues) & 
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)
MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)

---

### Post by arcanechaos on 2018-12-30
Thanks for the reply. Trying another image of 18.10 failed to work as well; however 18.04 threw the same error but proceeded to let me install on my external hard drive, so success! Anyone having the same problem I would recommend trying the 18.04 LTS image to see if that will let you proceed.

---

