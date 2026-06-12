---
title: "Ubuntu 10.04 Boot -- Constant Flickering"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by Wheels8257 on 2010-05-18
Hey guys,

When attempting to boot into Ubuntu 10.04, the screen constantly flickers. It'll stay off for about 2-3 seconds, then come back on for <1 second. This constantly occurs. When reaching the main screen (I think), I attempt to move into a TTY terminal, but the flicker continues. I have attempted to reset the X Server, stop the X server, etc., issue remains. The monitor does not turn off during this flickering. I am able to type, obviously.

Here are my system specs:

AMD Athlon 64 X2 Dual (6000+)
2.00 GB RAM
ATI Radeon HD2600 XT (x2, Crossfire)
HP w2207h 22" Monitor, connected via HDMI

I also have VGA inputs on the back of the monitor and can attempt to switch the input, but that requires me to dig through a box looking for a cable, so I figured I'd post this issue first.

Has anyone seen this issue, or know of a way to theoretically fix it?

Thanks,

Wheels

---

### Post by efflandt on 2010-05-18
Not sure if you are using default video driver or something else.  But the default for ATI in 10.04 is kernel mode setting (KMS) driver, instead of user space modules.  So you might try **nomodeset** kernel boot parameter and see if that helps.  That helps on my desktop with legacy ATI X1300 connected DVI to HDMI, and laptop with Radeon Mobiilty X1300.

Or for a USB drive booted on multiple computers you could use **radeon.modeset=0** as an alternate to just not use KMS for ATI video.

---

