---
title: "Installing Ubuntu 16.04.03 on Desktop, Cannot install due to repeating PCIe error"
date: 2017-09-05
forum: Installation &amp; Upgrades
---

### Post by wfu2 on 2017-09-05
Hi, 

I've been trying to install Ubuntu 16.04.03 but I've been getting this error:

```

PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e0(Reciever ID)

```

This happens when I try to press "Try Ubuntu", in which case the PC switches to a GRUB-like shell that repeatedly prints out the error and crashes the computer. When I try to install Ubuntu install of pressing the "try ubuntu" icon, I can go through the steps to install, but when I actually attempt installation the same error pops up and eventually my USB runs out of memory due to syslog. 

I searched up this problem and want to try to add kernel parameters pci=nomsi or pci=noaer, but I can't seem to get to the menu for that as I'm trying to install Ubuntu and don't have it installed yet. 

Any advice? I've been stuck on this problem for a while, will appreciate any advice on this issue!

---

### Post by BenginM on 2017-09-05
Hiya , the error seems to suggest an issue in communications with a PCIe device.. Something on that bridge device is not happy!reboot to the livecd/usb again, only this time don't try or install ubuntu..with the default kernel parameter, don't add any other. ones you are in the live session open a terminal and run $ journalctl -p 3 -xb

do you see the same error printed , if so note down the PCIe ID, something like : 
 pcieport 0000:00:1d.2:

then in a terminal run: $ *lspci -nn , and $  *lspci -tv[I]

[http://www.makelinux.net/ldd3/chp-12-sect-1](http://www.makelinux.net/ldd3/chp-12-sect-1)
[http://www.tldp.org/LDP/tlk/dd/pci.html](http://www.tldp.org/LDP/tlk/dd/pci.html)
[https://diego.assencio.com/?index=649b7a71b35fc7ad41e03b6d0e825f07](https://diego.assencio.com/?index=649b7a71b35fc7ad41e03b6d0e825f07)



[/I]

---

### Post by oldfred on 2017-09-06
Also what brand/model system?
What video card/chip?
UEFI or BIOS install?

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[/URL]
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

[URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

