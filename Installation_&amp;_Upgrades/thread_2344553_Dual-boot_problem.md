---
title: "Dual-boot problem"
date: 2016-11-26
forum: Installation &amp; Upgrades
---

### Post by wotsepotse on 2016-11-26
Hello everyone,

I try to install Ubuntu with dual boot on my Windows 10.
I have been using different method's but I still have not found a solution for mij problem.
The fact is about ubuntu (16.04.1 Desktop just - amd64). Which I have either burned to a CD and flashed on a USB stick.
So everything goes well I'll go to my BIOS and boot from my CD. If I chose the option Install / try Ubuntu goes tot the  purple-like screen and start the five dots to orangje colors to white and vice versa, so everything is still good. But about 20 seconds, he suddenly stops loading and freezes the screen. I can do nothing anymore from this point , I runned it for about 2 hours. But nothing happend.
My setup screen always freezes after a few seconds whether it's on a USB booted or a CD.
Do you know a solution for this? I have not found a solution for this.

Thanks in advance !

Further details on PC:
ASUS N551VW
x64
Intel I7-6700HQ
BIOS: UEFI
Nvidia Geforce GTX 960m

---

### Post by ubfan1 on 2016-11-26
Try the "nomodeset" option on the linux boot line.  Type "e" at the grub choices "try", etc. and edit the "nomodeset" where the "quiet nosplash" words are.  Once installed, you can then install the Nvidia drivers .  Search for nvidia here and askubuntu, lots of instructions on this video issue.

---

### Post by oldfred on 2016-11-26
If you are seeing purple screen not grub, then you are booting in BIOS mode. You want to be booting USB flash drive in UEFI boot mode.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

