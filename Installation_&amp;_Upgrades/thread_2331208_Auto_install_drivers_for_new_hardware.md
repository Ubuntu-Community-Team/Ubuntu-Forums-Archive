---
title: "Auto install drivers for new hardware?"
date: 2016-07-19
forum: Installation &amp; Upgrades
---

### Post by The Cog on 2016-07-19
I have installed Xubuntu on a USB drive (flash drive if it matters), and want to use this on multiple laptops. If I install it on one laptop, the installer removes all the un-needed drivers so that when I boot on the other laptop, the wifi does't work. There may be other hardware that has missing frivers too, but the wifi is the obvious one. 

Is there anything I can run that will do a hardware scan and select and install the right drivers, much as I guess the installer must do? I guess this question would apply to both installing new hardware in the same PC or booting the drive on a different system. Obviously, I don't want the "unused" drivers removed though - I want to be able to boot and work in either laptop.

---

### Post by him610 on 2016-07-19
Did you consider using identical wifi cards in the two laptops?

---

### Post by grahammechanical on 2016-07-19
Here is a guess.

Use ethernet and then Additional Drivers to install the appropriate WiFi driver for the second laptop. The original WiFi driver will be deactivated but not removed from the hard drive. Then it is a case of using Additional Drivers to switch WiFi drivers.

I base my guess on the fact that when I install a proprietary video driver and then activate the open source video driver the proprietary video driver is not removed from the system. I can re-activate it again. It does get listed as being no longer required and can be removed by autoremove.

Regards.

---

### Post by The Cog on 2016-07-20
> Did you consider using identical wifi cards in the two laptops?
I hadn't considered that. I think it would be a last resort.

> Use ethernet and then Additional Drivers...
Good idea. I'll try that, but it may be in a few day's time. After an update and upgrade this evening, the stick now boots to busybox, timeout waiting for the root device. So I'm going to have to reinstall from scratch.

---

