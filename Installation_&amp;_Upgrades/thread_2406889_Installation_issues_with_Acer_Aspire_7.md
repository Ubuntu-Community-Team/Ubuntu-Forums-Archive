---
title: "Installation issues with Acer Aspire 7"
date: 2018-11-27
forum: Installation &amp; Upgrades
---

### Post by grumpyowl on 2018-11-27
Hello to everyone! :)

I've tried (multiple times) to install single and/or dual boot with Win10 Ubuntu-based distros onto my laptop Acer Aspire 7 A715-72G-799G. Some of them didn't even make it to start in live mode, but a few I managed to install (Linux Mint Cinnamon and Ubuntu). But after that, when I was asked to reboot, the display froze. I had to manually reboot, got to the login screen and after input username and password, only I've got was a black screen with the cursor on it.

Forgot to mention, Win10 worked without any obstacles... unfortunately.

Laptot came with preinstalled Linpus without GUI.
Graphic card is nVidia GeForce GTX 1050 Ti

I've followed every single tutorial I could find, but nothing solved my problem.

Thanks in advance to everyone that would try to help and offer any advice!

Owl

---

### Post by oldfred on 2018-11-27
All Acer require "trust" setting in UEFI, if using UEFI.
Most have required UEFI update from Acer.

You normally need nomodeset boot parameter to boot installer & first boot or until you install nVidia driver from  Ubuntu repository.

These are all essentially the same, but some explain better or with more detail.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="https://community.acer.com/en/categories/predator"]https://community.acer.com/en/categories/predator

      [/URL]
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    [URL="https://community.acer.com/en/categories/predator"]
[/URL]

---

### Post by grumpyowl on 2018-11-30
Thank you very much, oldfred! 


The installation went smoothly. Dual boot (Kubuntu + win10) works perfectly fine. Finally, I can switch from my old laptop to a new one.


Best regards,
Owl

---

