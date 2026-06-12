---
title: "Wireless regressions in latest Lucid Beta 2 Updates"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DPic on 2010-04-12
I've been looking through launchpad for the relevant bug report but there  are so many wireless regressions it seems and i'm too much of a newb to figure out which is the one affecting me (or if this has been reported). Wireless was working fine on a clean install of Lucid Lynx beta 2 and after updating it no longer works. The applet says wireless is disabled and gives no option to enable it so i can't connect to wifi. 


Not sure if this helps but i can provide more details at request: 
~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:d7:03:95
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.10 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:dfdfe000-dfdfffff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:98:49:da
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:17 memory:dfdfd000-dfdfdfff

---

### Post by DPic on 2010-04-12
dammut nevermind. stupid wifi switch was hidden as a function key.

---

