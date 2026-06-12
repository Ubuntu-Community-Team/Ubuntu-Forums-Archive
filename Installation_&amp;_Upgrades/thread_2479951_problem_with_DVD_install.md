---
title: "problem with DVD install"
date: 2022-10-13
forum: Installation &amp; Upgrades
---

### Post by elson2 on 2022-10-13
I have been trying to install ubuntu (18.04 and 22.04) on a new i7 system. from a DVD burned with the iso file.  I get the same results with both, I get to the ubuntu deaktop background, with no boxes or menus.  I can do ctrl/alt/F3 and get to a login screen, but I want to do an OS install on a blank machine.  How do I do that? Is there some BIOS setting that is preventing it from going to the Welcome and install menu?  (On 22.04, a right mouse click will get me to a menu where I can open a terminal window.)

It would be nice to have the live installer just work, but if I knew what to type in the terminal, I'd be OK with that, too, to bring up the installer.  I actually need to install 18.04 for compatibility with some software packages that were linked with Buster.
Thanks in advance for any tips!
Jon

---

### Post by Impavidus on 2022-10-14
If this hardware is less than 5 years old (could be 3 years for 18.04.6), it may very well be that Ubuntu 18.04 doesn't have the drivers to handle that hardware. 18.04 will reach end of standard support in 6 months anyway. If less than a year old, it could even be that 22.04.1 doesn't handle it, so you may need 22.10 (to be released very soon).

The system does boot, but somehow the GUI fails, so that's pretty late in the chain. I can't rule out a graphics driver issue. What graphics hardware is in that computer? Maybe boot options related to graphics have some effect. Or it could be a bad burn.

---

### Post by ajgreeny on 2022-10-14
Did you check the .iso file that you burned to DVD and then check the DVD itself?

You may also find that using a USB thumb drive is a lot quicker and less likely to have these difficulties; very few users bother with DVDs for installing the OS these days!

---

### Post by elson2 on 2022-10-14
Yes, I checked the iso and the DVD, both OK.  Can somebody tell me what the installer GUI is?  I can try to just run that from the command line.  the system SEEMS to be fully working, although a bit slow from DVD.  I have seen graphics chip issues before, you generally just have a black screen.  I can get a terminal window up on the normal desktop background, although there's no taskbar.

---

### Post by yancek on 2022-10-14
The Ubuntu GUI installer is Ubiquity.

---

### Post by elson2 on 2022-10-14
OK, yes I figured that out.  Then, I tried installing Debian 10 (Buster) and the installer works, because the GUI appears to be using Curses.  But, X11 would not come up.  Apparently at least the older kernels/X drivers are not compatible with the Kabylake processor/graphics.  This looks like a major mess!
Jon

---

### Post by elson2 on 2022-10-19
OK, there is some serious kernel/Xorg issue with the Intel HD 630 graphics chipset.  To get a login screen on Debian 11, you have to give a grub option of i915.modeset=0 and then you are stuck at 800 x 600 screen resolution.  I have yet to get anything to work properly on this hardware.  I'm mostly just putting this here to complete the thread.

---

