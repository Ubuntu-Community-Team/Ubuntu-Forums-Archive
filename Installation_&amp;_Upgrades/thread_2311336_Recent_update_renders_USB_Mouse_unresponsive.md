---
title: "Recent update renders USB Mouse unresponsive"
date: 2016-01-26
forum: Installation &amp; Upgrades
---

### Post by John_Durgin on 2016-01-26
At some point in the last week or so, I've applied an update that causes my Logitech USB wireless mouse to not work.
Computer is a lenovo T-61 running Ubuntu 14.04

dmesg:
[ 1291.120103] usb 4-1: new low-speed USB device number 3 using uhci_hcd
[ 1291.297148] usb 4-1: New USB device found, idVendor=046d, idProduct=c51b
[ 1291.297160] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1291.297168] usb 4-1: Product: USB Receiver
[ 1291.297175] usb 4-1: Manufacturer: Logitech
[ 1291.326750] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input14
[ 1291.327211] hid-generic 0003:046D:C51B.0005: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-1/input0
[ 1291.342399] hid-generic 0003:046D:C51B.0006: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.1-1/input1

lsusb:
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=#0000cd]Bus 004 Device 003: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks[/COLOR]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I've tried the same mouse on a different computer (windows 10) and it works fine.
This only started happening in the last 7 days.

Any ideas?

---

### Post by steveo314 on 2016-02-01
See if this could be any help:
[http://www.webupd8.org/2013/07/pair-unpair-logitech-unifying-devices.html]("http://www.webupd8.org/2013/07/pair-unpair-logitech-unifying-devices.html")

---

