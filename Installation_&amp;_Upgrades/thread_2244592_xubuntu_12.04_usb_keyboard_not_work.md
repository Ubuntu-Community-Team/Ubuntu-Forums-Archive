---
title: "xubuntu 12.04 usb keyboard not work"
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by sathv on 2014-09-17
xubuntu 12.04 usb keyboard not work. Usb mouse work. Ps2 keyboard work. In BIOS USB legasy-enable

dmesg
..............
[  222.643313] usb 1-1.6: USB disconnect, device number 7
[  226.169046] usb 1-1.6: new low-speed USB device number 8 using ehci_hcd
[  226.288736] input: KB USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input15
[  226.288896] generic-usb 0003:04D9:A055.0009: input,hidraw0: USB HID  v1.10 Keyboard [KB USB Keyboard] on usb-0000:00:1a.0-1.6/input0
[  226.302669] generic-usb: probe of 0003:04D9:A055.000A failed with error -22
trikel-97@trikel97-desktop:~$ 

In xubuntu 14.04 keyboard work.

---

### Post by ibjsb4 on 2014-09-18
I have been lucky in the pass and fixed this in bios, as you have tried.  But though this link may give you some more ideas.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=usb+keyboard+not+recognized&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=usb+keyboard+not+recognized&sa=Search&cof=FORID:9)

---

