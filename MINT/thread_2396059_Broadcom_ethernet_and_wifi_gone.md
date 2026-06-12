---
title: "Broadcom ethernet and wifi gone"
date: 2018-07-10
forum: MINT
---

### Post by Otto-C on 2018-07-10
Dell 9400 80GB HDD 2 GB ram 32 bit Linux Mint 18.2 Sonya.
Ethernet and wifi quit following recent update.
How to recover?
tia
otto-c

With and without wifi donagle
$ lspci shows:
Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

Without wifi donagle

$ sudo lshw -C network

[sudo] password for bill: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:efdfc000-efdfffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:ef9fe000-ef9fffff


$ inxi -Fx
Network:   Card-1: Broadcom BCM4401-B0 100Base-TX bus-ID: 03:00.0
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
           Card-2: Broadcom BCM4311 802.11b/g WLAN bus-ID: 0c:00.0
           IF: N/A state: N/A mac: N/A

$ sudo ifconfig eth0 192.168.1.74
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device

---

### Post by howefield on 2018-07-10
Thread moved to the "*MINT*" forum.

---

