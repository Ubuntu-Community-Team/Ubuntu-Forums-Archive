---
title: "Lenovo T420 no boot in OS, no GRUB returns back to boot menu"
date: 2018-12-07
forum: Installation &amp; Upgrades
---

### Post by piromanneo2 on 2018-12-07
Hello 

Im having a big issues booting into the ubuntu desktop & server, I have tried every possible combination of bios settings (quick boot on-off, uefi boot on-off, forced legacy boot only, debug boot, diagnostic boot), disabled any security features of bios(fingerprint, intel security module etc..), sata is ahci, tried even different bios versions (1.46,1.48). 

Tried both ways of installation (legacy and uefi) and I still cant get system to boot. 

Also tried different ubuntu versions (16,17,18) desktop and server builds, and result is the same: system installs correctly, but grub bootloader is never shown, system RETURNS back to BSM (boot selection menu). I have unplugged the drive from laptop and put it in to a desktop. Fired up an installation, and system installs and also boots correctly. When have I put that disk back to laptop, there is a same story as before: OS does not boot, when GRUB bootloader should be loaded, system returns back to boot selection menu. 

Some forum threads recommend putting additional boot parameters in GRUB, but I even cant get to bootloader, as system returns back to bios. I have also tried to repair boot via ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) and repair is successful but system does not boot, same old story :(  

Im starting to loose my mind in this situation.

Windows on the other hand, boots just fine in both modes UEFI and Legacy. Thanks for helping me out.

---

### Post by yancek on 2018-12-07
The link to the Boot Repair site isn't going to help us to help you.  Try running it with the option to Create BootInfo Summary and post the link you get when it finishes.  This will give us some information on your system and boot files.  You indicate that you have some version of windows installed but not which one.  Did you read the Ubuntu documentation on dual-booting with windows on a UEFI machine, see the link below.

   [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by piromanneo2 on 2018-12-10
Windows version does not matters, since is installing and booting perfectly. To be clear I'm not aiming for dual boot. I've installed windows 7 and then windows 10(legacy and UEFI) just to verify that booting in windows is ok. Btw before any installations I've quick wiped the drive to exclude chance of conflicting partitions. Problem is as I indicated in first post is booting in Ubuntu both UEFI and Legacy installation. 

Will provide you a report later, but I'm afraid that it wont help much, because its repair is completed successfully and there is no errors or strange information as far as Im concerned.

---

### Post by oldfred on 2018-12-10
Have you updated UEFI form Lenovo for your system. And if SSD, updated its firmware?

Most brands use same UEFI with just different settings for different models with bigger difference between AMD & Intel motherboards.
But Lenovo does not seem as consistent, so not sure if any of these threads will help or not. Some now older & Ubuntu/kernel/driver issues should be improved.

T540 works but UEFI settings critical or it may brick reset w/ Switching "OS Optimized Defaults
 [https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[URL="http://ubuntuforums.org/showthread.php?t=2243715"]http://ubuntuforums.org/showthread.php?t=2243715
      [/URL]
 Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961) 
    
[URL="http://ubuntuforums.org/showthread.php?t=2243715"]
[/URL]

---

