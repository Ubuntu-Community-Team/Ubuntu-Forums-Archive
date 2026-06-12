---
title: "Gutsy install - restricted driver results in scrambled screen"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by The Shaolin on 2007-12-03
Hello, having some problems getting the proper video driver working for my video card.  (ATi Radeon x850xt)

Just upgraded to Gutsy.  The restricted driver manager popped up, I enabled it and restarted my computer.  After the ubuntu loading screen, I get a scrambled screen with beige random vertical bars, the monitor clicks like it's trying to change resolutions a few times, and then the cursor changes to an X.  A box pops up saying that I have to manually choose my video card.  If I choose Radeon FGLRX, I can get it to boot into 800x600 61hz, otherwise it's stuck at 640x480 85hz.  

I've tried installing the driver manually, and using envy.  All three give me the same result, which is leading me to believe the driver is installing properly in all 3 methods, but something is still very wrong.  

I'm stumped and open to suggestions, please help if you can!

---

### Post by jbt on 2007-12-04
> **The Shaolin said:**
> Hello, having some problems getting the proper video driver working for my video card.  (ATi Radeon x850xt)

Just upgraded to Gutsy.  The restricted driver manager popped up, I enabled it and restarted my computer.  After the ubuntu loading screen, I get a scrambled screen with beige random vertical bars, the monitor clicks like it's trying to change resolutions a few times, and then the cursor changes to an X.  A box pops up saying that I have to manually choose my video card.  If I choose Radeon FGLRX, I can get it to boot into 800x600 61hz, otherwise it's stuck at 640x480 85hz.  

I've tried installing the driver manually, and using envy.  All three give me the same result, which is leading me to believe the driver is installing properly in all 3 methods, but something is still very wrong.  

I'm stumped and open to suggestions, please help if you can!

I had something similar when I tried to use the ATI drivers with my card.
It seems that my card (radeon 7000) was not supported.
Maybe you have the same problem.

I fixed mine by using the "ati" driver.
Apparently this is a 'super driver' that selects the most appropriate ati driver.


Regards
JohnT

---

### Post by The Shaolin on 2007-12-06
Thank you for your response.

I'm assuming you mean that instead of selecting driver by model, you select driver by name?  I just tried that, picked the one that said "ATI (mach.....)"  and it worked just the same as before....I only have 800x600 and 640x480 resolution available and I cannot open Catalyst control center.

*sigh*.  As much as I hate XP, I don't know enough about Linux to make it work for me all the time.

---

### Post by jbt on 2007-12-07
> **The Shaolin said:**
> Thank you for your response.

I'm assuming you mean that instead of selecting driver by model, you select driver by name?  I just tried that, picked the one that said "ATI (mach.....)"  and it worked just the same as before....I only have 800x600 and 640x480 resolution available and I cannot open Catalyst control center.

*sigh*.  As much as I hate XP, I don't know enough about Linux to make it work for me all the time.

But, once you get it working - its so much better!
I've been battling with my dual screen config.
I've just downloaded the latest driver - and all of a sudden it was worth it !

I meant you to try the open source driver, rather than the ATI one.

[INDENT]*Choose driver by name: ati - ATI Mach8, Mach32,Mach64...*[/INDENT]

Should get you the right driver.

Make sure you select OpenSource Driver in the dropdown selection below.

You can check that you have the correct one by looking in /etc/X11/xorg.conf

[INDENT]Section "Device"
...
        Driver          "ati"
...
[/INDENT]
This should choose the right driver for you.

---

