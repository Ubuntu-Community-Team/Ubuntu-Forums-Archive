---
title: "Graphics Card driver"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by argoz17 on 2012-07-18
So I installed my unrestricted drivers for my nvidia card when i built my ubuntu 12.04 machine...when i rebooted it said on the screen after boot logo "mode unsupported" so i went ahead and reinstalled the OS, anyone know whats up? i have been searching the web trying to find out an answer.
Many thanks for any help.

---

### Post by UltimateCat on 2012-07-18
This might help you. This refers to the chipset-

[http://ubuntuforums.org/showthread.php?t=1778052](http://ubuntuforums.org/showthread.php?t=1778052)
[http://linux.bigresource.com/Ubuntu-Video-Mode-Not-Supported-get-it-to-work--zOVDKpQVN.html](http://linux.bigresource.com/Ubuntu-Video-Mode-Not-Supported-get-it-to-work--zOVDKpQVN.html)

This webpage refers to an artical in regard to unsuppoted mode at bootup:

[http://www.hardwareheaven.com/amd-graphics-cards/51735-help-unsupported-mode-boot-up.html](http://www.hardwareheaven.com/amd-graphics-cards/51735-help-unsupported-mode-boot-up.html)

Depending on your machine it may not have the RAM to handle your new card.  What kind of computer do you have?  A laptop? Desktop? How many GB and what manufacturer ( Dell, Lenovo, Sony etc...)

Try here too
[https://help.ubuntucom/community](https://help.ubuntucom/community)

---

### Post by prshah on 2012-07-18
> **argoz17 said:**
> So I installed my unrestricted drivers for my nvidia card when i built my ubuntu 12.04 machine...when i rebooted it said on the screen after boot logo "mode unsupported" so i went ahead and reinstalled the OS, anyone know whats up? i have been searching the web trying to find out an answer.


Are you still getting the "mode unsupported" error message?

Please press "Ctrl+Alt+Numpad-" or "Ctrl+Alt+Numpad+" repeatedly until you get a screen, it may be at a low resolution.

Typically, this error message indicates that the refresh rate / resolution combo is not suitable for the monitor; for example, if you are using a LCD monitor, you will have a typical refresh rate (usually 60Hz) and a "native resolution".

Using the above key-combo cycles through various resolutions. Please wait about 2-4 seconds between keypresses.

IMPORTANT NOTE: Every monitor manufacturer says that a monitor can be damaged by incorrect refresh rates. I have never had it happen to me yet, however, you follow this advice at your own risk, please.

Once you have a working display, run nvidia-settings as superuser, and choose the correct "native" resolution for your monitor (or suitable resolution+refresh rate if you are using a CRT).

Please post back with results.

---

### Post by argoz17 on 2012-07-22
Well Here are my specs.
My monitor is a 27" Samsung LCD TV. I'm using a VGA cable to connect. 
Graphics is a Zotec with Geforce 210 chipset.
Asrock ATX motherboard.
8 gigs of DDR3 RAM
AMD3+ quad core cpu
and 500gig HDD
---------------------
as you can see I have more than enough power for this thing, and under default settings with no driver my rez only gets up to 1360x768
---------------------------
and thank you so much for a reply

---

