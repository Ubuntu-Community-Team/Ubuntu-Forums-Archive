---
title: "Netgear MA401 card on 7.1 on Compaq Evo N800v"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by amalcolm on 2007-11-11
I recently installed Gutsy, replacing a working Feisty.

Initially the above card worked OK, but after using places->network to access another machine, network access with this card stopped working. Running lshw reveals that the card is disabled:
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0_rename
       serial: 00:09:5b:55:5f:52
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=
but I can't figure out how to re-enable. Nothing on the Network Settings panel helps, I can access the network via a wired network connection.

Any ideas ?

---

