---
title: "Freecom DVB-T usb stick"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by bjj on 2006-08-03
I am trying to install a Freecom DVB-T usb stick but it is not recognized by Kaffeine.
What is wrong?
Is some additional driver required?
Hereafter is what I get with some debugging commands.
_______________
/var/log/messages:

dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a firmware
dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) error while loading driver (-2)
usbcore: registered new driver dvb_usb_dtt200u
______________
$ cat /proc/version
Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
______________
$ lsusb
Bus 005 Device 003: ID 14aa:0222 AVerMedia (again) or C&E
__________
$ lsmod |grep dvb
dvb_usb_dtt200u         8836  0
dvb_usb                18952  1 dvb_usb_dtt200u
dvb_core               82984  1 dvb_usb
i2c_core               21904  2 i2c_acpi_ec,dvb_usb
dvb_pll                11012  1 dvb_usb
usbcore               129668  7 dvb_usb_dtt200u,dvb_usb,usb_storage,uhci_hcd,ehci_hcd,ohci_hcd
_________________

---

### Post by bjj on 2006-08-03
Finally it works excepted the sound.
I had to install the right driver: dvb-usb-wt220u-01.fw
How to get the sound working?

---

### Post by bjj on 2006-08-05
The sound requires libxine-extracodecs.
After installing that package everything works fine.

---

