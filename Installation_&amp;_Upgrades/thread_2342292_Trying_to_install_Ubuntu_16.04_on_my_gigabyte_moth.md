---
title: "Trying to install Ubuntu 16.04 on my gigabyte motherboard need help"
date: 2016-11-05
forum: Installation &amp; Upgrades
---

### Post by Supersonicx10 on 2016-11-05
Hello I haven't been here in a while but it looks like I need help installing Ubuntu 16.04on my system however, I'm using a gigabyte GA-MA785GM-US2H. I mean should install on there right? But to no dice I need to find out why it won't install on there, I even put a side HDD space for the install but nothing can you guys help me?

---

### Post by oldfred on 2016-11-05
I installed to my Gigabyte Intel based system without any issues. I did have to change some UEFI settings.
Also what video card/chip? AMD video cards/chips are in the middle of conversion from proprietary driver which has been obsoleted to new open source drive that does not yet support everything. 

Other models with AMD needed IOMMU settings in both UEFI and grub.
 Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by gordintoronto on 2016-11-05
Please tell us more than "no dice"? How did you detect that there was a problem?

I have a Gigabyte MA770T-UD3P which is just a bit older than your board. The biggest difference is that you have on-board video; have you tried "nomodeset"? My motherboard has run every version of Ubuntu since 10.04, although it has issues with ACPI, freezing after a random number of hours unless I specify a boot parameter of acpi=off.

I'm currently running 64-bit Linux Mint 18 Cinnamon from an SSD, and the performance is delightful with the Phenom II X2 CPU.

---

### Post by Supersonicx10 on 2016-11-06
> **oldfred said:**
> I installed to my Gigabyte Intel based system without any issues. I did have to change some UEFI settings.
Also what video card/chip? AMD video cards/chips are in the middle of conversion from proprietary driver which has been obsoleted to new open source drive that does not yet support everything. 

Other models with AMD needed IOMMU settings in both UEFI and grub.
 Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
It a Nvidia GeForce 550 Ti From the galaxy video card company it's a third party video card company.  


> **gordintoronto said:**
> Please tell us more than "no dice"? How did you detect that there was a problem?

I have a Gigabyte MA770T-UD3P which is just a bit older than your board. The biggest difference is that you have on-board video; have you tried "nomodeset"? My motherboard has run every version of Ubuntu since 10.04, although it has issues with ACPI, freezing after a random number of hours unless I specify a boot parameter of acpi=off.

I'm currently running 64-bit Linux Mint 18 Cinnamon from an SSD, and the performance is delightful with the Phenom II X2 CPU.

that's simple after the screen goes purple then black there a cursor at the top of my monitor. I go to press a key and nothing happens it looks like the system is locking up somehow.

---

### Post by oldfred on 2016-11-06
That is classic nVidia and you need the nomodeset.
You may need the IOMMU and the acpi=off also. You may have to try each and in various combinations to find what works.

Are you booting in BIOS or UEFI boot mode?
With UEFI you have grub menu, with BIOS you have to press any key when little accessiblity icons are on bottom of screen, then f6.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by Supersonicx10 on 2016-11-11
> **oldfred said:**
> That is classic nVidia and you need the nomodeset.
You may need the IOMMU and the acpi=off also. You may have to try each and in various combinations to find what works.

Are you booting in BIOS or UEFI boot mode?
With UEFI you have grub menu, with BIOS you have to press any key when little accessiblity icons are on bottom of screen, then f6.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

I'm going to boot from the BIOS why do you ask.

---

### Post by oldfred on 2016-11-11
If dual booting from Windows you have to use MBR for BIOS or gpt for UEFI.
But if on separate drive, then Ubuntu can boot from gpt with either UEFI or BIOS if you have correct supporting partitions.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

