---
title: "graphics driver issue"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by Lagos on 2007-11-23
i have an ati x1600 agp card, with the restricted driver, compiz, and XGL installed.  some basic compiz effects dont seem to be running as smoothly as they should be. i ran some diagnostics, and here is what i have... 

 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6473 (8.37.6)

so the ati driver seems to be loading correctly , but then i have this.... 

 glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


i know direct rendering was set to yes, right before i installed XGL to get compiz to work with my ati drivers.  how can i enable direct rendering?

---

