---
title: "Lucid error at boot"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ybytyruzu on 2010-04-06
Hi, 
I got the following message at boot:
drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?

After that the booting process continue without problem.
I have this error only with Lucid. On Karmic don't show that at boot.
I have a laptop with ATI Radeon Xpress 1100.

---

### Post by ybytyruzu on 2010-04-17
Hi, now I installed a fresh Beta2 and the error at boot is still there.
That error take about 10 or 15 seconds of my boot sequence, after that my boot is very fast.
Any idea?
Thanks

---

### Post by Didius Falco on 2010-04-17
There is a fairly new bug (April 14th) that been started on that error at launchpad. You should tick the "effects me too" link and subscribe to it. So far just one person has reported that they are effected by it - the more people that are affected, the sooner they devs are likely to look at it, and the more info they can get about it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843)

I read the report and it looks like the exact same thing that is affecting you...

Regards,

Didius

---

### Post by ybytyruzu on 2010-04-17
Hi Didius,

I will read the bug and subscribe to it.

Thank You!

---

### Post by Didius Falco on 2010-04-18
My pleasure. I hope it gets resolved quickly for those affected.

---

### Post by Eric Zurcher on 2010-04-20
I'm seeing the same error, with the Radeon XPress 200 chipset.

---

