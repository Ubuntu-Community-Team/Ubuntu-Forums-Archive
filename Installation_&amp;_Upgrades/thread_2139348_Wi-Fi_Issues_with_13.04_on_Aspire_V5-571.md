---
title: "Wi-Fi Issues with 13.04 on Aspire V5-571"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by Westonkd on 2013-04-26
Yesterday I upgraded from Ubuntu 12.10 to 13.04. I absolutely loved it until I realized the wireless connection would only last for about five minutes and then become unusable. I searched all over and ended up trying [this]("http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/") and [this]("http://www.techdrivein.com/2012/09/slow-erratic-wifi-ubuntu1204-fixed.html"). Nothing was working so I eventually reverted back to using 12.10 and everything is working great again. I would love to be using 13.04 right now so I am asking for help with this issue. 

Here is some of the info I got for my system after I re-installed 12.10, let me know if any other information would be helpful. Thanks!

```
*-network                      description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:02:00.2
       logical name: eth0
       version: 0a
       serial: 20:6a:8a:80:f3:58
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
  *-network
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 44:6d:57:b0:fc:5b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-27-generic firmware=N/A ip=10.7.190.29 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:f0500000-f057ffff memory:dfa00000-dfa0ffff



```

---

### Post by Westonkd on 2013-04-27
Any ideas? Thanks!

---

