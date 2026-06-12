---
title: "Display blanking hang"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by g-a-c on 2009-10-15
I seem to be having a problem whereby when my laptop engages the display power saving mode, after a while it will lock up. Network activity ceases (I can see my laptop timing out on IRC), the Caps Lock key doesn't light up when I hit it, and pressing a key or moving the mouse with the touchpad doesn't wake the laptop up. Only solution I've found is to hold the power button and power off.

The laptop is a Toshiba Portege A600, the graphics are Intel GM45, I just have a bog standard xorg.conf (can pastebin if required), and my Gnome Power Management settings are "Blank screen screensaver after 5 minutes" and "Put display to sleep after 5 minutes".

Is anyone else experiencing this? I want to report a bug, but I'm not sure which package to file it against, nor how to get any useful information from logfiles. Apport is useless as when the laptop locks up, I obviously can't run apport...

Thanks!

edit - I should note, my laptop never hangs while I'm actively using it, and if I wake the laptop up say a few seconds after the display goes into powersaving mode, it wakes up OK. This bug seems to be related to being in powersaving mode for a few minutes or more.

---

### Post by anselm on 2009-10-22
This also happens to me, I disabled power saving mode and set the screen saver to just blank screen, sometimes I have to do a hard reboot and sometimes it works fine haven't been able to see a pattern.

Dell Dimension 2400 Intel 845G chipset

---

### Post by g-a-c on 2009-10-22
A couple of days ago I did the opposite (disabled the blank screen screensaver but left display powersaving enabled) and I don't *seem* to have seen the problem since, although it was always somewhat intermittent...am waiting a little longer to see how it goes, I think.

---

