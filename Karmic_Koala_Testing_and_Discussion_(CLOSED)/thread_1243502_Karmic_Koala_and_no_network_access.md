---
title: "Karmic Koala and no network access"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by khristian on 2009-08-18
I just installed the Karmic Koala yesterday and found out I have no network access - not even the interfaces show up in "ifconfig -a". I did a lshw and it said: 
```
*-network UNCLAIMED
                description: Ethernet controller
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress cap_list
                configuration: latency=0
                resources: ioport:d800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff(prefetchable)

```

```
*-network UNCLAIMED
                description: Ethernet controller
                product: VT6105/VT6106S [Rhine-III]
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 8b
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master
                configuration: latency=64 maxlatency=8 mingnt=3
                resources: ioport:e800(size=256) memory:feaffc00-feaffcff
```

I tried modprobe'ing the r8169 and 8139too (which worked with the VIA nic) but nothing happened. What can I do?

---

### Post by superprash2003 on 2009-08-18
your network cards worked plug n play in 9.04?

---

### Post by khristian on 2009-08-18
yes, both of them.
Also, the reason why I have two is because the 8101e (onboard) is kinda buggy, and shuts down after a while (this happens on windows too, so it's not an issue now).

---

### Post by Patricrawley on 2009-08-19
I'm having the same issue, it is recognized in lspci. My wireless card also shows the network and lets me go through and set it up as I normally would in kubuntu 9.04 but now it just won't connect. I tried using iwconfig and the dhclient, but dhclient returned with no offers.

---

