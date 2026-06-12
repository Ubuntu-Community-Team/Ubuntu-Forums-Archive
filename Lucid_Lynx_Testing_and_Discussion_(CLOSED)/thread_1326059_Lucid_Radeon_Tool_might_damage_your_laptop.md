---
title: "Lucid Radeon Tool might damage your laptop"
date: 2009-11-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-11-14
Included in the latest Lucid updates is [[COLOR="Red"]pm-utils[/COLOR]]("http://packages.ubuntu.com/lucid/pm-utils"). Not knowing what it does and being of the inquisitive nature I decided to check out the package and found an interesting recommended package [[COLOR="Red"]radeontool[/COLOR]]("http://packages.ubuntu.com/lucid/radeontool") which can be used to control ATI based laptop backlights.  Under this package is states
> WARNING: Radeontool code has not been completely audited and may contain bugs that could damage your hardware. Use at your own risk.
How could I safely go about testing this ??? How is it audited to check for problems ?

---

### Post by dino99 on 2009-11-14
yes, big question !!!

Maybe can we test this on a virtual card embeded in a virtual system.

---

### Post by ranch hand on 2009-11-14
I would keep a kitten close at hand at all times and monitor its condition.

---

### Post by Rob2687 on 2009-11-14
That warning has been there since forever.

---

### Post by scradock on 2009-11-14
> **Rob2687 said:**
> That warning has been there since forever.
+1

The radeontool has been working on my HP Pavilion since I started using Ubuntu, several years ago.

---

### Post by woodbj on 2009-11-15
I found on this website while researching radeontool
> This tool should no longer be used, please use xrandr instead for setting external video modes. Backlight can be modified through sysfs
[http://www.thinkwiki.org/wiki/Radeontool](http://www.thinkwiki.org/wiki/Radeontool)

---

### Post by Kevbert on 2009-11-15
Thanks for that woodbj.  Seems strange that the developers are still working on (or have) a dodgy package in the repos when there's a better alternative.

---

