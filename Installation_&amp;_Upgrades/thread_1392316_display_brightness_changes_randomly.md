---
title: "display brightness changes randomly"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by nobswolf on 2010-01-27
After updating to 9.10 NBR on my MSI U90 it behaves like pressing the function keys "increase brightness" and "decrease brightness" continuously, including show the appropriate pop up.

I guess it is related to power management because it mainly happens while on battery.

How can I get rid of this problem?

---

### Post by KillaW0lf04 on 2010-02-09
Yep i got the exact same issue, could someone help us out?

Oh and mine also does the same thing while im on power

---

### Post by cryosphere on 2010-12-10
Yes, wtf, my msi wind 100 does the same thing, really annoying

---

### Post by cryosphere on 2010-12-10
Well I found a quick fix.  The brightness correlates with the cpu freq., meaning when your computer thinks you need to conserve power both cpu and screen brightness are turned down, and when your laptop is plugged in . .  anyway you get the point.  Anyway add an applet that lets you monitor CPU frequency - just right click on the panel, select "Add to Panel", pick "CPU Frequency Scaling Monitor".  When the applet comes up pick performance setting - anything but "on demand", apparently Ubuntu 9.10 has trouble figuring out the demand, or has some background process that keeps throttling CPU up and down.  A better fix would involve finding this process and fixing it.

Actually this is also discussed here in more detail [http://ubuntuforums.org/showthread.php?t=1316482](http://ubuntuforums.org/showthread.php?t=1316482)

it looks like some permutation of a bios update / upgrade to 10.04 takes care of this issue

---

