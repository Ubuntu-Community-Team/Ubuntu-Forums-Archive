---
title: "rt73 wireless dongle gives error but works flawlessly"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cb951303 on 2009-09-21
I've just switched to Karmic and my TP-Link TL-WN321G wireless usb dongle works better than Jaunty. It's more stable.

Here is the lsusb and lsmod outputs:
```

csu@desktop:~$ lsusb | grep Ralink
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
csu@desktop:~$ lsmod | grep rt73
rt73usb                29092  0 
crc_itu_t               2336  1 rt73usb
rt2x00usb              13600  2 rt73usb,rt2500usb
rt2x00lib              34624  3 rt73usb,rt2500usb,rt2x00usb

```

However, I also have these errors on dmesg:
```

[B][    7.436819] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[    7.436891] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.[/B]
[    7.436996] usbcore: registered new interface driver rt2500usb
[    7.912520] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.056286] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[    8.081674] phy1: Selected rate control algorithm 'minstrel'
[    8.082445] Registered led device: rt73usb-phy1::radio
[    8.082464] Registered led device: rt73usb-phy1::assoc
[    8.082484] Registered led device: rt73usb-phy1::quality
[    8.082933] usbcore: registered new interface driver rt73usb

```

Any ideas?

---

