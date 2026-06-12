---
title: "Can not install Ubuntu from boot media"
date: 2015-10-09
forum: Installation &amp; Upgrades
---

### Post by vdub20002 on 2015-10-09
I downloaded Ubuntu 15.04 and attempted to install it via USB and live CD. However, though I do see an initial purple screen, all I see afterward is a black screen. This also occurs with any older version of Ubuntu as well.

---

### Post by sudodus on 2015-10-09
Welcome to the Ubuntu Forums :-)

Please tell us about your computer. Otherwise we can only guess about the problem (I guess that it is a problem with the  graphics chip/card).

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It is also a good idea to check the downloaded iso file (that it was transferred correctly). Use ***md5sum*** to check it versus the listed string at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

What tools did you use to install from the iso file to the DVD and the USB drive? (A CD is too small for the Ubuntu iso file.)

Did you create the DVD disk and USB pendrive from Windows or from linux?

---

### Post by mastablasta on 2015-10-09
provide more info. also try nomodeset boot option - more here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by vdub20002 on 2015-10-09
Computer is a custom built
Intel i5 3.3 GHz
8 GB RAM
nVidia GeForce GTX 960 video card

I have a Wi-Fi adapter plugged in my computer... RealTek RTL8188CU WLAN 802.11n USB 2.0 Network Adapter

I used CDBurnerXP to burn the ISO file to a DVD and UNetbootin to create it using the USB drive, both were made in Windows.

---

### Post by vdub20002 on 2015-10-09
In this instance, I never saw any screen that would allow me to set a nomodeset boot option

---

### Post by oldfred on 2015-10-09
What motherboard?
Are you booting in UEFI mode, and you should see grub menu.
Or in BIOS mode press any key, and you get boot options and f6 lets you add nomodeset.

With UEFI and grub menu you have to add nomodeset manually. And you have to do that with first boot after install or until you install nVidia driver. Best to install using ppa, not from nVidia directly.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by vdub20002 on 2015-10-09
Mobo is an ASRock Z68 Extreme3 Gen3. I'm using BIOS mode since my hard drive wasn't converted to GPT to be able to use UEFI

---

### Post by oldfred on 2015-10-09
Asrock has issue with asmedia ports. Make sure no drive even DVD is connected to asmedia port.

Most of this is UEFI, but some issues may be common?
  Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)
ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6)
ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by vdub20002 on 2015-10-11
Still no luck. I converted from MBR to GPT and changed boot mode to UEFI. I still have the same problems trying to use a Ubuntu live disc.

---

### Post by oldfred on 2015-10-11
I do not know Asrock, but my Asus had many UEFI settings that I had to change.
I had a Windows setting which I turned off as I think that was really secure boot, but not labelled that way. I had to go into CSM to make UEFI settings. I had to allow USB boot. I turned off fast boot for both cold & warm(reboot).
I then updated UEFI to newest version which reset everything to defaults and I had to redo settings. :(

---

