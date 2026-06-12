---
title: "Wireless Problems in Intrepid"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by loligager on 2008-09-20
*-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:33:3f:34:aa
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:19:b4:08
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.6 multicast=yes wireless=IEEE 802.11bg


COMPUTER MODEL: TOSHIBA SATALITE A135 S7428

OK, i am able to connect to my router. I have to enter my key. Then it connects. I go to update the computer via synaptics, MY wireless becomes really slow. Then it disconnects, I go to reconnect. I enter password, it converts password into big text [might be hex] PAssword doesnt work, Back to square one, DId this 20 + times with repeated outcome of it converting password. In the ed, i am using the terminal to update, Seems to be going fine as of now

---

### Post by Death_Sargent on 2008-09-28
sounds to me like a signal strength issue but I can't really be 100% on that

---

