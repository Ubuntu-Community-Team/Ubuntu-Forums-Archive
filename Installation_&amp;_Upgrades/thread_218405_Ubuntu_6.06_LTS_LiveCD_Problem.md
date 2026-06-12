---
title: "Ubuntu 6.06 LTS LiveCD Problem"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by AstroTux on 2006-07-18
Hi,

I'm already a user of Gentoo Linux, and I am trying to run the Ubuntu Live DVD that came on the cover of Linux Format magazine.

It boots up fine, but when it goes to the graphical desktop, I hear the music, but the display instantly goes into screen blanking mode. This is NOT because the monitor is out of limits on resolution/scan rates, as the monitor displays a seperate screen stating this fact.

* Why is the display blanking?
* How can I change the X Server config so that it does not blank my display?

Hardware:

AMD Athlon XP 2600+
512Mb DDR333
128Mb GeForce 4 Ti4800SE (AGP)
VIA KT333 chipset
Hansol 900P 19" CRT (max res 2048x1536@60Hz)

Would I be correct in thinking that I can explore Ubuntu from the LiveCD as if it were installed?

Best regards,
AstroTux.

---

### Post by willd on 2006-08-09
Anyone any joy with this problem? I have the same problem on my Turion MT-40 laptop with ATI X700 gfx.

---

### Post by willd on 2006-08-12
[http://www.ubuntuforums.org/showthread.php?t=190036]("http://www.ubuntuforums.org/showthread.php?t=190036")

Putting this Option "MonitorLayout" "LVDS,Auto" in Xorg.conf worked for me.

---

