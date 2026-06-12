---
title: "nVidia corrupt display on reboot"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by zamolxis on 2010-12-03
I have a NV17 [GeForce4 420 Go] 10de:0175 (rev a3) card on a Toshiba Satellite 2140. After installing Maverick 10.10 with nouveau (default drivers), there is no option to upgrade to proprietary drivers (empty Additional Drivers list). That's probably a good thing, considering the incompatibility mentioned in bug 626974.

However, it seems that nouveau has a problem on reboot, as the display is horribly corrupted. Here's a video clip:
[http://www.youtube.com/watch?v=eFO061FAUyQ](http://www.youtube.com/watch?v=eFO061FAUyQ)

I attached the output of dmesg | grep nouveau

Upgrading to the proprietary driver is not an option because of bug 626974. Is there anything I can do so that the display is no longer corrupt on reboot?

---

