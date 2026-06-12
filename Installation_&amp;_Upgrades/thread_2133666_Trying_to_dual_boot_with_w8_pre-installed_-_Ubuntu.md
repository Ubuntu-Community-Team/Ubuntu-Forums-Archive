---
title: "Trying to dual boot with w8 pre-installed - Ubuntu disk boots to a black screen."
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by brentNZ on 2013-04-08
[COLOR=#333333][FONT=Ubuntu]I'm trying to install Ubuntu alongside Windows 8 - Windows 8 came pre-installed on the machine.
The laptop model is the MSI GX60. Hardware can be found at this link: [http://www.playtech.co.nz/afawcs0139235/CATID=368/ID=20002/SID=854103852/productdetails.html#DetailedSpecifications](http://www.playtech.co.nz/afawcs0139235/CATID=368/ID=20002/SID=854103852/productdetails.html#DetailedSpecifications)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I've tried installing both the 32 and 64 bit versions by DVD. I've also tried to install from a USB. When I tried to install Ubuntu I just got stuck at a black screen. As a last resort I tried to install Ubuntu through WUBI, this method also failed. I later found the Wubi isn't supported in windows 8. Source: [http://askubuntu.com/questions/225048/is-wubi-for-windows-8](http://askubuntu.com/questions/225048/is-wubi-for-windows-8).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I went to the IRC Ubuntu channel for help and was told to check out these documents:
1)[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
2)[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
This is what I have tried:
- booted comp
-hit del to enter bios
-disabled secure boot. (this allowed me to get to the efi grub screen. Prior to this i just got the black screen)
-hit e over the install ubuntu option
-added nomodeset as a boot parameter and deleted quiet splash: linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity nomodeset -- and then hit f10 to boot
-tried the same for radeon.nomodeset=1:linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity radeos.nomodeset=1 -- and hit f10 to boot
- I also tried nomodeset with quiet splash.
All options just booted to a black screen
I'm not sure what to try next?
Any help would be greatly appreciated.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Thanks,
Brent[/FONT][/COLOR]

---

### Post by oldfred on 2013-04-09
UEFI is only supported with the 64bit versions of 12.10 & now 12.04.2.
It looks like you have AMD with ATI/AMD video. I have nVidia so am not as sure of settings you may need. Many of the very new systems need both a video parameter and other boot parameters. Replace quiet splash with the generic or Radeon settings and perhaps others like pci=nomsi, but see list below.
   

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

      
 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

 [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll


 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

---

