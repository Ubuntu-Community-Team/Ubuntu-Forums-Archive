---
title: "ATI Radeon 9200 / RV280 low resolution"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by huffy318 on 2008-05-31
I upgraded to 8.04 from 7.10, and now i can't get my resolution above 800x600.

The video card is ATI Radeon 9200 / RV280 .  The monitor is a Scanport GEM GL-1920B and work up to 1280 x 1024.

I am using the default driver, and have tried it with and without xorg.conf (i was not using xorg.conf on 7.10).

When I bootup, I get a popup saying it couldn't detect either the card, the monitor, or both.  It lets me configure, and the test looks ok, but when I log in, low res.

Are there any tricks to get this working?

Here are some readouts: 

~ $  glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

~ $ glxinfo | grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I attached the verbose output of glxinfo if it helps.

Doe the no direct rendering mean my card is not supported for the default drivers?

Thanks,
Eric

---

### Post by huffy318 on 2008-06-01
I decided that it would be a good time for a fresh install anyway, so i did.

The live version and install detected the monitor and video card w/o a problem, so now it is working fine.

I don't know why that worked, but the config routine during bootup didn't.

So, it's solved for me, but no real answer on why the update didn't work.

Eric

---

