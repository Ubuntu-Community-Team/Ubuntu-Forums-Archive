---
title: "Ubuntu upgrade presents blank pink screen after login"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by donrudi on 2014-04-21
I just upgraded from 12.04 LTS to 14.04 LTS (64 bit) in my dual-boot XP-Linux Core 2 Duo machine. I get a normal graphical login screen, but after entering my password, a blank pink screen appears with only "Ubuntu 14.04 LTS" in the lower left hand corner -- no icons, no menu bar. Yes, my video card is powered by the dreaded NVIDIA chipset...:(

---

### Post by grahammechanical on 2014-04-21
After entering the password the login panel should disappear (that is happening) and Compiz compositor should take over control and load the Unity user interface. That is not happening I think. You can try at the Grub boot menu selecting the Advance Options for Ubuntu sub-menu and then select Recovery mode. At the Recovery menu select Resume. That should load to a login and desktop without using a proprietary video driver.

If you get to a desktop go to System Settings>Software and Updates>Additional Drivers tab and experiment with another driver. Perhaps the open source video driver - Nouveau.

Regards.

---

### Post by donrudi on 2014-04-21
Thank you for your input. Unfortunately. Advanced Options > Recovery Mode > Resume produced the same results - a blank pink screen with the version in the lower left corner loaded. I also tried "Run in Fail Safe Graphics Mode."  A dialog came up "What would you like to do" but I couldn't select anything because the mouse and keyboard froze. I had to do a hard reset to exit.

---

