---
title: "Linux not booting from clean USB or no mouse when boots from old system SSD"
date: 2015-08-30
forum: Installation &amp; Upgrades
---

### Post by dgm5555 on 2015-08-30
[COLOR=#111111][FONT=Arial][B]I've just built a new system with the following components.  It boots from ubuntu 14.04 64bit from the SSD I took directly from my previous system,  but there is no mouse. 
I've tried to boot from USB with Ubuntu 64bit and 32bit with various 14. and 15. versions and also tried Mint, but they all fail after a minute or so of boot info (my old system was fully booted in approx 18secs)
Main components are:
AMD FX8320 Black Edition 8 Core
[/B][/FONT][/COLOR][COLOR=#111111][FONT=Arial][B]Gigabyte 990FXA-UD3 SKT-AM3+ Motherboard
[/B][/FONT][/COLOR][COLOR=#111111][FONT=Arial][B]Palit GTX750Ti KalmX Graphic Card (2GB, GRA, PCX)
[/B][/FONT][/COLOR][COLOR=#111111][FONT=Arial][B]HyperX FURY Series 8GB (2x 4GB) DDR3 1866MHz CL10 DIMM

It boots Win 10 and functions normally.

Hope someone can help...
[/B][/FONT][/COLOR]

---

### Post by oldfred on 2015-08-31
It seems all Gigabyte boards require the IOMMU setting changed and [COLOR=#008000]*iommu=soft*[/COLOR] boot parameter added to boot.
And nVidia often needs [COLOR=#006400]*nomodeset*[/COLOR] boot parameter.

You may need the iommu setting as a permanent setting but should only need the nomodeset to boot live installer & first boot or until you install nVidia proprietary driver.

 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

[/URL]
 Maxwell 750 - kernel 3.15 or newer required
[http://ubuntuforums.org/showthread.php?t=2292419](http://ubuntuforums.org/showthread.php?t=2292419)
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)

Ubuntu just started its own ppa, which eventually may make it possible to install drivers at same time as you install system.

 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa.




[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

