---
title: "Unable to boot Ubuntu 19.10 USB  on Alienware 51m GPU Graphcis card"
date: 2020-01-06
forum: Installation &amp; Upgrades
---

### Post by ajay443 on 2020-01-06
I created a Ubuntu 19.10 USB stick using balenaEtcher software. The USB stick with Ubuntu 19.10 is working fine with another system. So I decided to dual boot my [Alienware Area 51m]("https://www.dell.com/en-us/shop/cty/pdp/spd/alienware-17-area51m-laptop") with Ubuntu 19.10. I see graphics error, some thing like in the below picture. How to troubleshoot this ? Am I missing something here to install the Ubuntu 19.10, apart from disabling the secure boot in windows 10?


 [ATTACH=CONFIG]284751[/ATTACH]

---

### Post by oldfred on 2020-01-06
If you have nVidia, you need nomodeset when you boot.
I believe it is with 19.10, it will offer to install proprietary drivers now including nVidia driver. 
Before you had to boot install with nomodeset until you installed proprietary driver, but then can install nVidia drivers.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Issues often common across many versions of same brand, or similar Dell also.
You probably need UEFI update and if SSD firmware update.
If using Windows add AHCI driver, then change drives from RAID/Intel SRT to AHCI (unless RAID 0 and then other issues).

Alienware Area 51 R4 16.04 UEFI update
[https://ubuntuforums.org/showthread.php?t=2397456](https://ubuntuforums.org/showthread.php?t=2397456)
[https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4](https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4)
Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)

---

### Post by ajay443 on 2020-01-10
adding nomodeset to boot menu solved the issue of black screen. thank you. 

I have other problems regarding SSD, I will probably ask as a different thread.

---

