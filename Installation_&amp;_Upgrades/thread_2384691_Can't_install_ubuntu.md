---
title: "Can't install ubuntu"
date: 2018-02-10
forum: Installation &amp; Upgrades
---

### Post by monjessenstein on 2018-02-10
Hey guys, just created an account as I'm having trouble installing ubuntu on my pc. I downloaded the latest ubuntu version and made a bootable USB with rufus, but when I boot from it on my pc I basicly get the equivalent of a command prompt. Thanks in advance!

---

### Post by oldfred on 2018-02-10
UEFI or BIOS system?
What brand/model system?
What video card/chip?

If UEFI hardware, you have two boot options from UEFI.
So you know whether booted in UEFI or BIOS/CSM/Legacy mode this shows both screens.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If BIOS only system you should get the purple screen shown in above link.
But if you need boot parameters, often required for video, you may need enter, then f6 when first booting with tiny icons at bottom of screen.

---

### Post by monjessenstein on 2018-02-10
Probably not a UEFI, since it's a dimension 9200 I turned into a cheap gaming pc. Video card is a 6950. I'll take a look at some settings in the bios, though I don't get a purple screen at startup.

---

### Post by oldfred on 2018-02-10
PC Systems over 5 years old are usually BIOS, only a few started with UEFI just before Windows 8 came out. 
Apple converted to EFI (before UEFI) when it converted to Intel chips.

If less than 2GB of RAM, you may need lighterweight flavors.
Is system 64 bit?
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors) 
    
Is the 6950 nVidia? Then you need nomodeset. 
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

