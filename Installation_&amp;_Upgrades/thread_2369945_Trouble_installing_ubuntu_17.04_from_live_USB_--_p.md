---
title: "Trouble installing ubuntu 17.04 from live USB -- possible bluetooth issues"
date: 2017-08-28
forum: Installation &amp; Upgrades
---

### Post by tjoel on 2017-08-28
I am running into issues when I attempt to install ubuntu via live usb onto my Gigabyte P15FV5-NE1 laptop. It looks to be related to bluetooth but I am not knowledgeable enough to know where to go from there. I have attempted to install on multiple usb drives, using both rufus and etcher. This same issue comes up when I try installing lubuntu and elementary as well. Any help is appreciated, thanks!

[ATTACH=CONFIG]276534[/ATTACH]

---

### Post by oldfred on 2017-08-29
At top of screen is comments on unclean file system.
You left Windows fast start up on, and need to have that off.

It looks like your system has nVidia, so you need nomodeset until you can install proprietary driver in the full install.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

See also link in my signature for UEFI install info.

---

