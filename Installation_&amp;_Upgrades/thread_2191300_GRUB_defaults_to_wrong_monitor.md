---
title: "GRUB defaults to wrong monitor"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by gabmontes on 2013-12-01
I have a desktop PC with an ATI Radeon HD 5450, a monitor attached to the DVI output an a TV to the HDMI port. It dual-boots Ubuntu 13.10 and Windows 8.1 using GRUB 2 (automatically set up during Ubuntu installation).

The problem is that after turning on the PC, both monitors show POST information but then GRUB menu is displayed on the TV while the monitor turns blank.

Is there any way to configure GRUB to show the OS selection menu on the monitor or on both TV and monitor? GRUB documentation and configuration options apparently do not help to achieve this. PC BIOS has apparently nothing to do here either as POST shows up in both screens but then GRUB chooses the TV.

Thanks in advance!

Gabriel

---

### Post by RvL on 2014-02-12
Don't know if you're still looking for a solution, but I've found one.

In /etc/default/grub, the line setting the resolution for GRUB is commented out. Enable this line by removing the # and save the file.

Next run sudo update-grub and you're done.

---

