---
title: "how i got my xserver to work again"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by hockman5 on 2009-12-17
Haven't been upgrading to the new release because when I tried it before, I could never get my xserver to work again. So today I decided to do the upgrade and if it doesn't work , remove Ubuntu.
What I did was booted into recovery. Copied the /etc/X11/xorg.conf.failsafe overwriting xorg.conf. Then I rebooted. I had the xserver but with no compiz stuff. So I went into system preferences and selected the appearance setting. I changed the appearance to include animations and such (the second selection from the bottom) and then it said I needed to install the driver for my graphics card (ATI). It then installed the driver.I had to reboot again. Went back into appearance, did the same selection and everything works now. I am able to go into the Compiz Fusion and select the items I want (wobbly windows, Desktop Cube, etc). This was a simple fix that I could not get help on through the many post of asking for it. If this post helps just one person, than it is worth it.

---

