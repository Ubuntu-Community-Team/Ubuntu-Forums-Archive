---
title: "Resultion 1680x1050 revert to 1280x1024 after upgrade to 11.04"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by carlin on 2011-05-29
Hi guys,

I had installed Ubuntu 10.10 and Screen resolution of 1680x1050.

After upgrade to 11.04, screen resolution revert to 1280x1024. Monitor preferences does not show 1680x1050 option.
Ubuntu installs Unify desktop.

Doing the following commands, the resolution changed to 1680x1050, but desktop shows a top and a right bands as black. The launcher, the dash, and top system row (the one that has the home button and logout button and others) shows ok (dash shows ok over the black band). If I move windows over the "blacks bands" they doesn't show (as if the black bands where out of desktop limits).
[INDENT]xrandr --newmode "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
xrandr --addmode VGA1 1680x1050_60.00
[/INDENT]

I attached the hardware configuration, and the xorg.conf used with Ubuntu 10.10.

I've tried removing the xorg.conf and with different configurations for the newmode (taken from gtf, cvt, and other pages).

Thanks for you help.
Carlin

---

