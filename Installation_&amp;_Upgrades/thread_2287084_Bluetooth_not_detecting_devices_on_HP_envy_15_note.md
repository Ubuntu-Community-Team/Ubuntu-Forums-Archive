---
title: "Bluetooth not detecting devices on HP envy 15 notebook"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by Akul_Narang on 2015-07-16
I'm facing problem with my bluetooth as it is not able to find/detect BT  devices. I'm using ubuntu 14.04 install on HP envy 15 notebook.

output of dmesg | egrep -i bluetooth

[   23.091438] Bluetooth: Core ver 2.17
[   23.091453] Bluetooth: HCI device and connection manager initialized
[   23.091459] Bluetooth: HCI socket layer initialized
[   23.091461] Bluetooth: L2CAP socket layer initialized
[   23.091464] Bluetooth: SCO socket layer initialized
[   23.161727] Bluetooth: can't load firmware, may not work correctly
[   25.168881] Bluetooth: hci0 command 0x1003 tx timeout
[   31.084131] Bluetooth: RFCOMM TTY layer initialized
[   31.084141] Bluetooth: RFCOMM socket layer initialized
[   31.084145] Bluetooth: RFCOMM ver 1.11
[   31.108736] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.108739] Bluetooth: BNEP filters: protocol multicast
[   31.108746] Bluetooth: BNEP socket layer initialized
[   33.353907] Bluetooth: hci0 command 0x1003 tx timeout

output of uname -r:
3.13.0-57-generic

---

