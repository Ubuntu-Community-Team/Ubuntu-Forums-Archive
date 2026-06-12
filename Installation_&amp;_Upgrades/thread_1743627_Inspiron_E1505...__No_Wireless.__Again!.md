---
title: "Inspiron E1505...  No Wireless.  Again!"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by eldgog on 2011-04-29
So.  I upgraded.  Now I cannot use wireless.  lshw -C network gives me this:

*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:ecffc000-ecffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:61:c0:17
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.79 latency=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ecbfe000-ecbfffff


however, i cannot see anywhere that i have my old wlan0 connection configured.  i have done this before, YEARS ago and my config survived many upgrades, but i have settled into a bit of a complacency and long since forgot how to amend this.  boo.  so any help would be great, particularly in lays-terms.

---

### Post by mörgæs on 2011-04-29
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

