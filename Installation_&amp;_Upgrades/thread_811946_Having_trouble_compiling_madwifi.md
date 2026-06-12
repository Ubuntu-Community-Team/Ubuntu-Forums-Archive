---
title: "Having trouble compiling madwifi"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by jobo1313 on 2008-05-29
Last week I installed Ubuntu 8.04 on my Sony vaio VGN-NR220E. But the wireless didn't work. The driver didn't show up. I read that I needed to install madwifi. I downloaded it and tried to compile it. Then a bunch of errors came up saying that it couldn't find the c headers. I tried multiple codes such as:
gksudo aptitude install build-essential
gksudo apt-get install gcc
None of these worked.

I was told to type in lshw -C network I don't see why
But anyway here it is:
~$ lshw -C network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: 88E8039 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 15
serial: 00:1a:80:25:a4:a0
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.0.3 latency=0 module=sky2 multicast=yes
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:06:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0

Help

---

### Post by zvacet on 2008-05-29
You alleady started thread with same question,so don´t double post.It is confusing for you and for ones who want to help you.Lok for answers in your original thread.

---

