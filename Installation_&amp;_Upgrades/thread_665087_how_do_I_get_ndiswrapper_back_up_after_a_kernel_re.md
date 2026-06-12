---
title: "how do I get ndiswrapper back up after a kernel recompile?"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by 0mcg0 on 2008-01-11
I've reconfigured/recompiled the kernel and it comes up fine but no wlan or sound.   The old generic kernel uses ndiswrapper  for the wireless (Broadcom chip on a HP Laptop).
In the custom kernel it seems like all the ndis stuff and driver is properly installed but nothing can seem to find wlan0 and associate it with ndiswrapper so that I can configure the wireless.  Everything still works fine in the generic kernel.   Any clues on how to get wlan0 back for the custom kernel?

---

### Post by 0mcg0 on 2008-01-11
BTW this is on gutsy which seems to work fine but with a few problems that I can work around.  It can't hibernate at all. If I leave the laptop open I think power management kicks in, even though I've tried to disable it, and locks things up, I just close the top and leave it plugged in and everything is fine.

---

### Post by zero-9376 on 2008-01-11
you might have to recompile the ndiswrapper and alsa modules to match your new kernel.

---

### Post by vloris on 2008-06-11
There is a problem in hardy if you compile your own kernel, the package ndiswrapper-source is not available.

---

