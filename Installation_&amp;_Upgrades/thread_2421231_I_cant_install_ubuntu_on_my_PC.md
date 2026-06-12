---
title: "I cant install ubuntu on my PC"
date: 2019-06-18
forum: Installation &amp; Upgrades
---

### Post by fredmuch on 2019-06-18
Hello, guys,

I try to install Ubuntu 19.04 but I have a problem. I am use windows 10 on my PC but I want use Ubuntu. When it booted isntallation process , show this screen and stuck it. My BIOS have latest version, I tried it in RAID and IDE mode, but same problem. Change sata port, boot from DVD or USB device still same problem. How to fix?
[URL="http://photos.app.goo.gl/f6dgDhR62Po3SzfU9"]
http://photos.app.goo.gl/f6dgDhR62Po3SzfU9[/URL]

---

### Post by oldfred on 2019-06-18
It says AHCI driver not available.

You need to change in UEFI/BIOS settings to AHCI from RAID or Intel RST.
Most systems also need UEFI/BIOS updates and if an SSD, firmware update.

What brand/model system?
What video card/chip?

---

### Post by fredmuch on 2019-06-19
I have changed to AHCI mode Disable fast boot. But it doesnt work.
I have Asus Rampage IV Black Edition motherboard installed windows 10.
Video card is Nvidia GTX 770

---

### Post by oldfred on 2019-06-19
With nVidia you also need nomodeset boot parameter for live installer & first boot or until you install nVidia driver from Ubuntu repository. Newest versions of Ubuntu are now installing nVidia driver during install.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

My Asus Z97 motherboard needs several UEFI setting changes. 
UEFI is similar across many Asus models, bigger difference if Intel or AMD.
       
 Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu)

---

