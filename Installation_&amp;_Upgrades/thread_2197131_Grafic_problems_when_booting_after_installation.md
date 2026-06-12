---
title: "Grafic problems when booting after installation"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by Hellboy256 on 2014-01-02
I've installed Ubuntu 12.04 on my new Lenovo E540 successfully. But when restarting and choosing Ubuntu in the GRUB menu the screen remains black. I still get the login screen because I can here the drums!
I've already tried to set the parameter in the GRUB menu '[...]quick splash[...]' to '[...]nomodeset[...]' but that didn't help...
I gues it's a problem with the graphic card??

---

### Post by fantab on 2014-01-02
Ubuntu 13.10 is quite friendly with the newer hardware, 12.04 is not so much. Try Ubuntu 13.10.

What graphic card or cards do you have?
Are you dual booting? What version of other OS you have?

---

### Post by Hellboy256 on 2014-01-02
I've tried 13.10 to but there I just receive a black screen with a blinking white stripe I don't even get to the login part!?
The graphic card is: NVIDIA GeForce GT 740M
Yes I am dual booting the other is Windows 7

---

### Post by fantab on 2014-01-02
You should use 'nomodeset' to boot the DVD/USB.

[QUOTE= 'oldfred']**Black Screen/ Video Modes**
This usually required with AMD or nVidia.
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Newer systems may have this setting:
Also turn off one Video mode or Intel settings in UEFI/BIOS like Intel NIC if USB flash not working.

Some Laptops need this in place of "quiet splash":
       *acpi_osi=Linux acpi_backlight=vendor*

Some laptops just have backlight set way down, press f key to make it brighter[/QUOTE]

Was Win7 pre-installed? How is it booting, in BIOS mode or UEFI mode?

---

