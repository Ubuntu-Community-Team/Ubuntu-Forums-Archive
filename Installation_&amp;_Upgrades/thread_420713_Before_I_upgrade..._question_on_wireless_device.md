---
title: "Before I upgrade... question on wireless device"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Lukeg on 2007-04-23
I am currently using 6.10 on my computer and with a good deal of effort have gotten my wg111v2 usb wireless dongle to properly (within reason) function.

The results of:```
readlink /sys/class/net/wlan0/device/driver/module
``` suggest that it is currently working with the r8187 driver, though I do not know what version.

When I tried out 7.04 on my other computer (really my brother's computer) with an identical dongle (chipset is the same), I was successfully able to access internet via the dongle while using the LiveCD, and shortly after installation, but after I preformed an update, the device ceased to work.

I am not immediately concerned with my brother's computer, but I am concerned with mine.  If I update to feisty via adept updater (I'm using kubuntu), do I run the risk of my dongle not working, or will the update leave such things untouched?

I noticed that 7.04 ubuntu seemed to have a different way of handling wireless stuff, something about wmaster0, but I don't know.  Any guidance would be appreciated.

---

### Post by Lukeg on 2007-04-23
Perhaps there is some way to preform the update and see if everything works, then revert if it doesn't?

---

