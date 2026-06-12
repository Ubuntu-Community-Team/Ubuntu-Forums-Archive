---
title: "Cannot select correct screen resolution with"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by petroslam on 2009-11-19
Hi!

I've just installed Ubuntu 9.10 on my media center - everything works fine except for my screen resolution.

I need a resolution of 1176x664 to fit everything on my screen but the closest option is 1200x800. 

I've installed the recommended Nvidia drivers and also looked into Xrandr and the Xorg config file (which doesn't exist and cannot be created using sudo Xorg -configure)

Can someone please help? I'm desperate!!


Cheers,
Peter

---

### Post by efflandt on 2009-11-19
What is the actual or supported resolution of your monitor or display?  It may also depend upon what video modes your card and driver support.

With an older actual 1280x720 27" HDTV that normally only supports HDTV modes or PC Video modes (up to 1280x1024) on an older PC, X in 9.10 defaulted to an odd 1152x864 4:3 mode.  But it offered a 1360x768 mode that I was surprised works well with my HDTV.  In this case it is an ATI AGP card, but I just used default drivers and have not installed any restricted or proprietary driver for it.

---

