---
title: "Ubuntu 18.04 on Macbook 2011 WIFI Problem"
date: 2018-08-04
forum: Installation &amp; Upgrades
---

### Post by joetheeskimo14 on 2018-08-04
Hi All

So i have got fed up with how slow my macbook 2011 late model is being since all the updates apple are throwing out there. I have had ubuntu in the past (approx 7 years ago on a windows based PC). I finally got it installed, had to create a DVD with ubuntu ISO burned on it. 

Any way the install has now overwritten OS and the machine just runs on ubuntu now. 

I tried to connect to the internet and in the Ubuntu settings under "WI-FI" it says "No WI-FI Adapter Found"

i have gone into the terminal and tried the following
[LIST]
[*]rfkill list
[/LIST]

the result was: 
0: hci0: Bluetooth
Soft Blocked: No
Hard Blocked: No

[LIST]
[*]ifconfig
[/LIST]
the result was 
Command 'ifconfig' not found, but can be installed with: sudo apt install net-tools

[LIST]
[*]lspci -nnk|grep -iA3 net
[/LIST]

the result was 
02:00.0 Ethernet controller {0200]: Broadcom Limited Netxtreme BCM57765 Gigabit
Ethernet PCI1 [14e4:16b4] (rev 10)
Subsystem: broadcom limited netxtreme bcm57765 gigabit ethernet pcie [14e4:16b4]
kernel driver in use: tg3
Kernel modules: tg3
02:00:1 SD Host Controller [0805]: broadcom limited bcm57765/57785 sdxc/mmc card reader [14e4:16bc] (rev 10)
03:00:0 Network controller [0280]: broadcom limited bcm4331 802.11a/b/g/n [14e4:4331] (rev 02)
subsytem: Apple Inc. Airport Extreme[106b:00d6]
kernel driver in use: bcma-pci-bridge
kernal modules: bcma


Can anyone please help.

---

