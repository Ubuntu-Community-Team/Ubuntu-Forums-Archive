---
title: "can not install ubuntu 16.04 via usb"
date: 2017-02-13
forum: Installation &amp; Upgrades
---

### Post by felipe222 on 2017-02-13
Hello I need to install ubuntu in my new PC.Ihave already installed windows.WHen I try to install from USB it says "invalid gbrt: can not map memory" then the screen turns black and it has been in that stat for more than 8 hours. Before that i have tried changing the port ad the usb pendrive but i always got the same message and the everlasting black screen.Any suggestions will be well received.Thank you for your attention.


PS: I have an intel i7 7700k cpu and a msi z270 gaming pro carbon motherboard.

---

### Post by Geoffrey_Arndt on 2017-02-13
What are the graphics specs?

---

### Post by oldfred on 2017-02-14
What video card? Or are you using Intel video?
Or have you tried just Intel video?

Older MSI cards needed fast boot in UEFI off. May still be an issue.

My Z97 motherboard required lots of UEFI settings changes to boot Ubuntu in UEFI mode.
       [http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2) 
    
This Gigabyte board Z170 needed 
one must select "IGFX" instead of "PCI Slot 1"
[http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04](http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04)

---

### Post by felipe222 on 2017-02-14
Hi I am currently using  the intel graphics of my i7 I am waiting a little bit more to buy a graphics card. Thank you i will check the links. It might be of importance that i am currently using 1 nvme m.2 and one sata m.2. I am currently using a 32 inches tv screen as a monitor, I do not know if that could also affect .

---

### Post by oldfred on 2017-02-14
Normally use of nomodeset was just for AMD & nVidia new cards to get a low quality graphics.

But I recently saw a user use nomodeset with new Intel video. Does not hurt to try.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by Geoffrey_Arndt on 2017-02-16
Try install just using one  connected drive.   Especially if multi-partitions on each drive (like root on one and home on the other).

---

