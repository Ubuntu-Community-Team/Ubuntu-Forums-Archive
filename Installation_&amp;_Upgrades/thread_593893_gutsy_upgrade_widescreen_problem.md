---
title: "gutsy upgrade widescreen problem"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by eb207 on 2007-10-27
hello,

I upgraded from fiesty to gutsy, and have been having problems with widescreen.

my video card is: Intel Corporation 82Q963/Q965 Integrated Graphics Controller

In feisty, I was running 1920x1200. I was using the 915resolution package to make it work. Now after the upgrade, using my old xorg.conf file, the best screen resolution i'm getting is 1600x1200.

915resolution is still installed, as is xserver-xorg-video-intel.

Any suggestions? It seems the solution must involve having the right packages installed. I tried removeing 915resolution, but this didn't help.

Other people have posted about widescreen problems, but none with exactly my setup, and none of thing things in those posts has helped me.

thanks.

---

### Post by trappist on 2007-11-14
If you know how to use 915resolution, just do your thing with it and "downgrade" your video driver from "intel" to "i810".  That's what I had to do, after trying everything else.

---

