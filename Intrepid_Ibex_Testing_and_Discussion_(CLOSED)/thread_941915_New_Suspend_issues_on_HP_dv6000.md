---
title: "New Suspend issues on HP dv6000"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ladr0n on 2008-10-08
Hey guys,

I'm running Intrepid on my dv 6000.  Overall, the hardware support is pretty good - for the first time, I've been able to get my broadcom wireless card to work without ndiswrapper.  

However, it seems that suspend is not working properly, which is a regression from Hardy.  When I attempt to suspend it appears to work (system drops into a low power state, etc), but upon resume, the backlight doesn't turn on and the kernel appears to have hung (doesn't respond to any commands, hitting caps lock doesn't get the light to come on).  

Possibly important specs are:  
nVidia geforce 8400 with the new nVidia proprietary driver
Broadcom 4311 wireless with the new proprietary driver.  I think it's b43.

Can anyone confirm this/suggest a solution?  If I can't get it to work by this weekend I'll report a bug, but I want to make sure it's not something I'm doing wrong first.

---

### Post by jasonpeinko on 2008-10-15
I have thet exact same problem, but it was amazing to get the b43 driver working without ndiswrapper.

---

