---
title: "kernel 2.6.32-20 No Wireless"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jaoc223 on 2010-03-22
I have an issue with the red exclamation mark in gnome nm, my signal is fine in mac osx, and seems to be fine on beta1, I read somewhere on the forums a few days ago that this is a bug in nm. My other issue is I have wireless working, but after turning off my box and coming back to it the next morning nm wireless shows I'm connected, but cannot resolve any hosts, I then connect wired, unplug and then wireless is ok. Anyone else having this issue? I'm using beta 1 with the 2.6.32-14 kernel, I installed from an alpha3 build dated Mar.15th, and updated to beta1, because the 2.6.32-20 kernel wouldn't allow me to work with wireless when I installed from the beta1 release dated Mar.17th. I'm really puzzled as to why my wireless works ok all day and then the next morning it seems to need a wired jump start to get it going. I should mention at night when I shutdown I power my router off by unplugging the A/C, and plug it back in the morning. I thought maybe unplugging my router was causing the problem with wireless needing a wired jump start, but I just tested this by shutting down my computer unplugging the A/C, then unplugging the A/C from the router, I waited about 10 minutes plugged comp and router back in, booted up and wireless is connecting, as I said I thought unplugging my router at night was maybe causing my issue. Any thoughts or ideas are greatly appreciated. Thanks in advance.

from lsmod i have this: 

*-network 
description: Wireless interface
product: BCM4328 802.11a/b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth1
version: 05
serial: 00:1f:5b:d1:1b:b8
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.7 latency=0 multicast=yes wireless=IEEE 802.11abgn
resources: irq:16 memory:50200000-50203fff

*-network
description: Ethernet interface
product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth0
version: 13
serial: 00:22:41:21:3b:e4
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
resources: irq:29 memory:50100000-50103fff ioport:5000(size=256) memory:50d00000-50d1ffff(prefetchable)

under my hardware drivers STA Broadcom I see this:

This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.

Is BCM4328 802.11a/b/g/n supported here?


from blacklist.conf i see this: 

# replaced by b43 and ssb.
blacklist bcm43xx

Does that mean my BCM4328 802.11a/b/g/n is not being loaded when lucid boots?

Edit. I left my router plugged in lastnight, and this morning when I logged on to my machine wireless connected without a hitch. I think the problem here is the kernel 2.6.32-20 released on beta1. The solution for me was when I updated to beta1, I updated everything except the kernel. Hope this helps someone.
I'm still wondering though, as stated above is the BCM4328 trying to be blacklisted when Ubuntu is loading up.

---

