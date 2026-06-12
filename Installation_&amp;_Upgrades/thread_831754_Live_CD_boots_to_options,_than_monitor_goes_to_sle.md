---
title: "Live CD boots to options, than monitor goes to sleep.  DVi to HDMI problem?"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by taseedorf on 2008-06-17
Situation: I attempt to boot and install kubuntu from a live cd.
I can get to the first options screen, however, after trying to install my monitor goes to sleep.  I know this is because of my connection to my monitor being a hdmi on my pc, to an dvi on my monitor. Anyway to fix this??? If it is a drm issue, can someone explain it to me?

---

### Post by dstew on 2008-06-17
If you see the options screen, you know that plain vga will give you an image on your monitor. My guess is that the Live CD kernel does not have the software to run the graphics adapter properly.

You can force the kernel to use plain vga (or vesa) using kernel parameters. I think there might be a Safe Graphics Mode option if you choose F6 at the opening menu, try that. If that doesn't work, you can add kernel parameters using F6 also. Add to the end of the kernel line **vga=791** or **vesa=force** and hit enter, then 'b' to boot.

Another alternative is to use the Alternate Install CD. It installs the same desktop system, but uses a text-based installer. Get it from the Download Ubuntu page, check the box below the Start Download button.

Also, make sure you have checked the CD for errors (opening menu choice).

---

