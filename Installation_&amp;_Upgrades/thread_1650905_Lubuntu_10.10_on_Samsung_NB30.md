---
title: "Lubuntu 10.10 on Samsung NB30"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by jlparsons on 2010-12-22
Hi folks, I've managed to install Lubuntu 10.10 on a Samsung NB30 with everything (but suspend) working.  Personally I think it suits this machine perfectly but I'm sure some will disagree.  However there are two niggles during installation of lubuntu which can be very annoying and caused me to have to start over (twice!), so I thought I'd document the process here (let me know if this is the wrong place!).

Firstly, the USB startup disk you must create to install lubuntu on this netbook must be set up as non-persistent - if you're using the standard ubuntu usb startup disk creator, check the box that reads "changes will be lost on restart" (or similar).  Otherwise you get applications crashing during the install and it all goes pear shaped.

To install the system just boot from the USB startup disk and install as you normally would for any flavour of ubuntu, then restart your system and lubuntu fires up as normal.  Next you'll have to get the touchscreen, backlight controls and hotkeys working so follow the instructions on this page which is a how-to on installing ubuntu (not lubuntu) on the nb30: "http://www.greenhughes.com/content/installing-ubuntu-1010-samsung-nb30-touchscreen-netbook" with one key difference: Wi-Fi works out of the box on lubuntu 10.10 and installing the samsung-wireless package as instructed will disable it.  I skipped that step altogether (the second time around) and moved right on to the next.  I've not had any issues at all with whatever driver works out of the box so I figure if it ain't broke, don't fix it.

That is all!  You now should have a fully functional and much faster netbook.  In fact if this is the first OS you've installed after getting rid of windows 7 starter edition (which the netbook ships with) then prepare to be amazed...

The only thing I never got working is suspend/resume which is a bit annoying.   I know suspend/resume issues are common on laptops running linux so I've just learned to live with it, just remember to disable suspend altogether by telling the power management system not to suspend when the lid is closed or power is low (to find power settings, right click the battery icon, you need to unplug the cable for it to appear if you can't find it!).

---

### Post by samo615 on 2011-01-11
Screen brightness controls do not work.Also, I have written a script to set my resolution to a higher level. If anyone knows a way to do this, please reply.

gedit screenres.sh

#!/bin/bash
xrandr --output LVDS1 --mode 1024x600 --scale 1.25x1.25

Make it executable:
chmod +x <filename>

go to System'->'Preferences'->'Startup Applications' and add it to the list.

---

### Post by jlparsons on 2011-02-02
Never had an issue with brightness controls, mine worked dandy.  Check up to date mobo firmware?

---

### Post by samo615 on 2011-02-03
I can adjust before I boot into Linux, but then it is set. Regarding the firmware, the only update that I have found provided by Samsung executes in a Windows only environment. Although, I have NOT had success with 3 Windows PE environments via USB.

 What method did you use to flash your BIOS?

> **jlparsons said:**
> Never had an issue with brightness controls, mine worked dandy.  Check up to date mobo firmware?

---

### Post by jlparsons on 2011-02-05
> **samo615 said:**
> I can adjust before I boot into Linux, but then it is set. Regarding the firmware, the only update that I have found provided by Samsung executes in a Windows only environment. Although, I have NOT had success with 3 Windows PE environments via USB.

 What method did you use to flash your BIOS?

Mine was already at the most recent version on purchase, can't help there sorry. :(

---

### Post by scottrosenquist on 2011-02-06
Mine was fixed by adding acpi_backlight=vendor after quiet splash in the grub entry. Dunno what my bios is at. Hope that helps.

---

