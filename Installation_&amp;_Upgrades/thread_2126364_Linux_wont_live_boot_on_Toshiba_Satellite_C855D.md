---
title: "Linux wont live boot on Toshiba Satellite C855D"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by 265494 on 2013-03-16
My dad has a Toshiba Satellite C855D-S5105. He wants me to install Linux on it since he doesn't like windows 8. I have tried to boot Linux Mint 13/14 and Ubuntu 12.04.2/12.10 (all 64 bit) off a usb drive, all of them got the same result. A prompt came up asking me what I wanted to do. I selected the option for live booting on all of the distros. Each time it went to a black screen where it sat, nothing ever happened.

 Is there anything I can do to get at least one of the distros (preferably an LTS one) to work?

Here are the specs: 
CPU: AMD E-300 APU Dual core (1.3ghz)
GPU: Radeon HD 6310 384mb @500MHz
Ram: 4GB 1600 MHz
HDD: 300 GB 5400 RPM

BTW, I have Secure Boot disabled(this laptop uses UEFI). It also seems that there is no option to dvd boot on this computer, even though it has a dvd drive.

---

### Post by oldfred on 2013-03-18
Some have reported with UEFI that it only booted from flash drive, others only could boot from DVD. 
But your issue seems to be video. I have nVidia and have to use nomodeset, not sure it that works with AMD or not?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

      
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Some systems also only install in BIOS mode, and then have to use Boot-Repair to convert to UEFI mode.

---

### Post by 265494 on 2013-03-18
Thanks, I will try it out next time im at my Dad's house.

---

### Post by aarons6 on 2013-03-18
you can also try the xforcevesa switch

---

