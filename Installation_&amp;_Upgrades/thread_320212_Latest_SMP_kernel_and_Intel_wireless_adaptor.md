---
title: "Latest SMP kernel and Intel wireless adaptor"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by fredj on 2006-12-16
I installed Ubuntu 6.06 on a Samsung Q35 notebook and after some tweaking everything
seems to work well including my WPA wireless network. Since I have a core duo 
I wanted to install the 686-SMP kernel but when I boot into this my wireless network
adapter disappears. Some clue as to why this is happening is given by the 
lshw -C NETWORK command. Here is the output from this in both kernels

IN 386 Kernel

  *-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:df:da:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.0.5m firmware=13.0 1:0 () ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d4000000-d4000fff irq:177


**********************************************************
IN 686 Kernel

  *-network
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945
       resources: iomemory:d4000000-d4000fff irq:177

It seems that the SMP kernel doesn't detect the wireless adaptor correctly.
Does anybody have any idea how I can correct this?

---

### Post by emperon on 2006-12-17
AFAIK there was a incompatibility between Nvidia drivers and wirless when you use SMP. Also this issue should have been resolved in 2.6.19

---

