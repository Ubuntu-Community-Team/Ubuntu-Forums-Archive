---
title: "Intel AC 8260 Wifi Card Not able to install drivers"
date: 2015-12-05
forum: Installation &amp; Upgrades
---

### Post by campbell3 on 2015-12-05
Hey, has anyone had trouble installing drivers with an intel wifi card? I have downloaded the drivers, but can't figure out how to install them. Any help would be appreciated.

---

### Post by vuo on 2015-12-06
Intel doen't seem to be offering downloadable drivers for Linux for it (yet): [https://downloadcenter.intel.com/product/86068/Intel-Dual-Band-Wireless-AC-8260](https://downloadcenter.intel.com/product/86068/Intel-Dual-Band-Wireless-AC-8260)

Have you tried *Settings &#8594; Software & Updates &#8594; Additional Drivers*?

Maybe it's to early and support still has to land in kernel/firmware yet.

*EDIT:*
[This]("https://askubuntu.com/questions/693109/intel-wireless-8260-unclaimed-network") might help. (related: [Bug #1517375 &#8220;Missing PCI IDs for Intel 8260 wireless hw&#8221;]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1517375"))

---

### Post by vuo on 2015-12-17
You may be in luck with the *iwlwifi* driver now: A fix to said [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1517375") has just been [released]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1517375/comments/3") with todays linux kernel upgrade for *buntu Wily Werewolf (4.2.0-21.25). *(via [change log]("https://launchpad.net/ubuntu/wily/+source/linux/+changelog"))*

Try in terminal: [FONT=courier new]sudo apt update ; sudo apt full-upgrade[/FONT]

---

