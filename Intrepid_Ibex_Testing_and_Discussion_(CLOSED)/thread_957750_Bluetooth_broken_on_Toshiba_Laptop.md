---
title: "Bluetooth broken on Toshiba Laptop"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dna on 2008-10-24
The bluetooth adapter on my Toshiba Protege has stopped working since upgrading from Hardy.
The old way was to press fn-F8 to activate it (off by default in the bios) but now that does nothing.
When I reboot into the last kernel on my box from Hardy (2.6.24-19-generic) and press the fn-F8 key combination it causes a hard lockup where I have to hold in the power button to restart.
The bluetooth kernel subsystem seems to be loading;
```
[   28.461760] Bluetooth: Core ver 2.13
[   28.462893] Bluetooth: HCI device and connection manager initialized
[   28.462899] Bluetooth: HCI socket layer initialized
[   28.488858] Bluetooth: L2CAP ver 2.11
[   28.488870] Bluetooth: L2CAP socket layer initialized
[   28.506457] Bluetooth: SCO (Voice Link) ver 0.6
[   28.506469] Bluetooth: SCO socket layer initialized
[   28.546851] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.546865] Bluetooth: BNEP filters: protocol multicast
[   28.630169] Bluetooth: RFCOMM socket layer initialized
[   28.630193] Bluetooth: RFCOMM TTY layer initialized
[   28.630199] Bluetooth: RFCOMM ver 1.10
```
The bluetooth adapter doesn't show up in 'lsusb' due to it not being turned on by fn-F8.

---

### Post by dna on 2008-10-26
In case anyone was wondering I tracked this to the new tlsup module that replaced the toshiba_acpi kernel module.

It appears that it won't be fixed until post-release with a regression to the toshiba_acpi module which, apparently, was completely removed from the ubuntu kernel tree.

Doesn't really explain why it hard locked with the old kernel unless it's a hal issue as well. Even modprobing the tlsup module hard locks the box so I can't do any further testing until after they put toshiba_acpi back in the official tree since I don't feel like doing any kernel hacking to fix the old patch.

Oh well...

---

