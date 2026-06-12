---
title: "VIA Chrome fails on 9.10 and 1280x1024 resolution with DELL 1907FP"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by udippel on 2009-12-11
This is FYI.

Via Chrome (KM800) cannot be set to 1280x1024 on 9.10. Over.
You need to create a basic xorg.conf, and add the horizontal and vertical frequencies of the LCD, since it also fails to detect it. (XP on the same box works okay, so it's a driver problem.)

Here are all the gory details for documentary purposes:
I have been fighting for days with a fresh install of Ubuntu 9.10 on a machine with DELL 1907FP attached. Already the LiveCD does not do more than 800x600, despite of the DELL having a native 1280x1024 resolution. 
The same after installation.

Then the odyssey began:
xrandr with all its beauty would and could not activate that mode neither. On the command line it talked about some crtc problem; when applying with 'Display' it would say "Could not set the configuration for CRTC113".
My usual last resort also failed: Recovery, and Xorg -configure. It would bring up a screen with Xorg -config xorg.conf.new, but a totally black screen. Alas, we have no more Ctrl-Alt-Backslash, so I had to reset the machine hard, a number of times.

As last resort, I copied a basic xorg.conf that I have in store for failsafe configuration to that box. (Also, unfortunately this skeleton has been removed from more recent distributions.)
The only setting it has, is 'driver vesa'. It booted, as to be expected to 800x600. Then I added the horizontal and vertical frequencies of the monitor, and - voilà - with 'Display' I could select a number of modes, including 1280x1024. 
Still, vesa is crap-slow; worse than chrome. So I only uncommented the line with 'driver vesa', and the problem was back: the monitor displaying 'invalid resolution'. And here comes the point: 'Display' does offer higher and lower resolutions, but no 1280x1024. So I could select and apply 1280x960. 

Lond story, short result: 
1. There is a bug in the openchrome driver
2. It would still be good, to ship with a basic, inactive. xorg.conf for eventual adjustments
3. Ctrl-Alt-Backslash was retired too early.

Hope, this helps someone, one day.

---

