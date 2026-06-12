---
title: "GRUB Boot loader doesn't appear after ubuntu/windows 10 dual installation"
date: 2018-10-24
forum: Installation &amp; Upgrades
---

### Post by jorge.ruiz.qui on 2018-10-24
Hi there!

As you can see, this is my very first post in the community and unfortunately is because of a problem. 

I've completed an instalation of ubuntu in a laptop where Windows 10 was already installed. I've chosen the dual mode in order to be able to run both Windows and Ubuntu as needed.

The installation finished successfully and after login for the first time in ubuntu, I decided to reboot the system. In that first time, a nice GRUB boot loader menu appeared correctly, showing the Ubuntu installation together with Windows. I selected to start Windows in order to make sure it was still running fine and started with no problems. After that, I powered off the laptop thinking that the GRUB menu was going the first thing I will see on screen but Windows was started directly as usual instead.

Given that my BIOS has secure boot enabled and boot mode set as ***UEFI ***(see attachments), I created a pendrive (using rufus) with the ubuntu iso image and GPT-UEFI as parameters for partition schema and target system (see attachments).

I've some questions:
[LIST]
[*]¿Is there something wrong with my BIOS or RUFUS configuration?
[*]¿Does ubuntu 18.10 support UEFI mode? (I understand that yes...)
[*]¿Do I need to do any extra work (fixing grub for instance)?
[/LIST]

Thanks very much in advance!

---

### Post by oldfred on 2018-10-24
What brand & model system? Some need special settings, but if able to boot first time, it still should work.

Until someone can review report, do not run any auto fix.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jorge.ruiz.qui on 2018-10-25
Thanks ***[COLOR=#000000]oldfred [/COLOR]***for your reply.

> [COLOR=#000000]What brand & model system?[/COLOR]

The system is basically Sony VAIO , Model SVE1512Y1ESI with MS Windows 10 Home edition installed. Please, see attachment for more details.

I tried to start the laptop again using the same USB for installation and the only option apart from Install again is "check disc", which I run already but with no results.

Thanks again!

---

### Post by oldfred on 2018-10-25
Sony was one that violated UEFI spec that says NOT to use description as part of boot. And of course only valid description is "Windows Boot Manager".
Have you updated UEFI to latest version for your system. Some other systems do now work better that had same issues after UEFI updates.

Boot-Repair now copies shimx64.efi to bootx64.efi to be a fallback or hard drive entry that usually works, if you have a drive entry.
Before users had to manually copy.
       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)

Older but similar issues:
       
 One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589) 
             HOWTO: Sony Vaio Pro 13 DualBoot (Win 8 + Ubuntu Trusty 14.04) SecureBoot Wifi LVM
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580)
 Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
[http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive](http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive)

---

