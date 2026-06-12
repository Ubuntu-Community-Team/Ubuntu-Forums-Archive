---
title: "Logitech Unifying receiver doesn't work in Kubuntu 16.04 LTS"
date: 2017-11-06
forum: Installation &amp; Upgrades
---

### Post by ertrum on 2017-11-06
I installed Kubuntu 16.04 LTS on a Dell 9010.
After the install, lsusb shows ```
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
```

dmesg, grepping for usb, shows the following
```
[    1.451502] usb 2-1.6: Product: USB Receiver
[    1.451503] usb 2-1.6: Manufacturer: Logitech
[    1.460351] usbcore: registered new interface driver usbhid
[    1.460353] usbhid: USB HID core driver
[    1.555346] usb 2-1.5.3: new high-speed USB device number 5 using ehci-pci
[    1.647750] usb 2-1.5.3: New USB device found, idVendor=0424, idProduct=2524
[    1.647752] usb 2-1.5.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.647966] hub 2-1.5.3:1.0: USB hub found

```

All of this looks ok to me, but the keyboard and mouse aren't connecting.
But, when I run solaar 0.9.2 to display the linked devices, I get: 
```
solaar-cli show -v
solaar-cli: error: Logitech receiver not found
```
 
which seems a bit inconsistent at best.

I have also tried upower, which also doesn't show anything useful.

I know that the Unifying receiver, keyboard and mouse all work - they work fine on a PC.

Where do I go next?

---

### Post by ertrum on 2017-11-29
re-re-re installing ubuntu fixed this, don't know why.

---

