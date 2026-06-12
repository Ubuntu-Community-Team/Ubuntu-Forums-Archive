---
title: "Ubuntu and Ubuntu-Gnome 13.04 live USB hangs at boot on Acer Aspire One 725"
date: 2013-09-05
forum: Installation &amp; Upgrades
---

### Post by kay2 on 2013-09-05
I am trying to install Ubuntu on a new laptop that came with Windows 8. I've disabled UEFI and enabled booting from USB, but when the laptop loads from the USB it hangs at "SYSLINUX 4.06 EDD 2012-10-23 Copyright (C) 1994-2012 H Peter Anvin". I've tested the USB on a known good system and it shows the boot menu and loads the OS without a problem, but on this system it hangs at boot with the copyright info. This has happened with both Ubuntu and Ubuntu-Gnome images.

Can anyone give me some ideas on what to troubleshoot here? I've never had an issue like this on any system I've worked with and I don't know where to start.

---

### Post by oldfred on 2013-09-06
If possible better to boot in UEFI mode not BIOS mode anyway. Then you are booting with grub not syslinux.
You cannot easily dual boot if Windows is UEFI and Ubuntu is BIOS as each time you have to go into UEFI/BIOS and turn on/off UEFI.

       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Different models, but may be somewhat similar.

 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

