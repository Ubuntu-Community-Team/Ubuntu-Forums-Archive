---
title: "Intel graphics - sluggish"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Irayo on 2008-10-16
I have a Dell Inspiron 1100, which has worked okay in other versions of Linux (and earlier versions of Ubuntu/Kubuntu).  The machine is based on the Intel 855GM chipset with integrated graphics, if I recall correctly.

My issue is that the laptop runs horribly slow.  Simple programs like Terminal sometimes go "dark" and become unresponsive just when doing simple tasks.  Slightly more complex programs like Firefox become very difficult to use because the screen only redraws once every second or so.

Xorg uses between 20 and 60% of the CPU power when the computer is entirely idle (except for `top` running in a Terminal).  Firefox uses 50% or more when on any page that has animated graphics (flash, GIFs).  Sometimes when opening menus or new windows there's display corruption.  Things like moving windows causes minor skipping.

I believe the issue is related to the graphics driver.  I modified xorg.conf to load the `intel` driver but it did not help.  Looking at the log, I can see that the driver is indeed loaded (along with glx and other acceleration drivers) but it doesn't seem to be having much effect.  I can attach Xorg.0.log later, but it does not list any particular error messages and I can't do it until tonight.  CPU throttling is off, the laptop is cool, so heat shouldn't be a problem.

This issue has been persistant for a few weeks, now.  I've upgraded all packages to the newest versions as of four days ago and I'm in the process of upgrading again now.


Additional:  Driver detects card, "intel(0): VESA VBE OEM Product: Intel(r)852GM/852GME/855GM/855GME Graphics Chip Accelerated VGA BIOS"
Says "Will not try to enable page flipping" and "Triple buffering disabled".  These generally greatly influce performance.

---

