---
title: "Dual booting with windows 8"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by Jonathan_Steyfkens on 2014-07-23
so I made a bootable usb from my portable usb drive. Everytime I try to install lubuntu or ubuntu I just get a black screen and the whole pc freezes. I need to force it to power off. Anyone has an idea on how to fix?

I'm running on an i7-3770 , gtx 770 with an asrock mobo.

---

### Post by oldfred on 2014-07-23
What video? Intel's or do you also have video card?

       ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[URL="https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order"]https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order

[http://www.phoronix.com/scan.php?page=article&item=asrock_z97_extreme6&num=1](http://www.phoronix.com/scan.php?page=article&item=asrock_z97_extreme6&num=1)
[/URL]

---

### Post by Jonathan_Steyfkens on 2014-07-24
I'm using a nvidia GPU GTX 770 so not the intel integrated one.

---

### Post by oldfred on 2014-07-24
If booting in UEFI mode you get grub menu and after installing at grub menu you need to add nomodeset.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

If installing in BIOS mode, later it also shows first boot grub edit.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If screen not correct this workaround may work:
      
 When you see you are in the desktop but no icon or bar, right click to change desktop background
When the window appear, click all settings, now you see the system settings window.

Screen shot of installing nVidia driver.


Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia or AMD... fglrx-upgrade

---

### Post by Jonathan_Steyfkens on 2014-07-25
That's the problem. I don't even get to that point. I press "try without installing" and all I get is a black screen. No installation options, nothing. I already tried the nomodeset thing.

---

### Post by oldfred on 2014-07-25
Do you have drive plugged into the asmedia port? Those generally do not work as Linux does not have a driver.

---

### Post by Jonathan_Steyfkens on 2014-07-25
I don't think so. I have to check it out. Never heard of asmedia ports.
I just did some checking. I'm on an asrock B75 Pro3-M hope that helps a little.

---

### Post by oldfred on 2014-07-25
Only one Intel port and two ASmedia?

 [http://www.asrock.com/mb/Intel/B75%20Pro3-M/?cat=Specifications](http://www.asrock.com/mb/Intel/B75%20Pro3-M/?cat=Specifications)
- 1 x SATA3 6.0 Gb/s connector by Intel® B75, supports NCQ, AHCI and Hot Plug functions
- 2 x SATA3 6.0 Gb/s connectors by ASMedia ASM1061, support NCQ, AHCI and Hot Plug functions

---

### Post by Jonathan_Steyfkens on 2014-07-25
ok, So I found these sata3_A0 and A1 ports. And changed those devices to the other ones I had free. The normal SATA ports. Now I can boot it. I'll try installing it right now. Thanks for the help! If I need more help I'll let you know ;)

---

