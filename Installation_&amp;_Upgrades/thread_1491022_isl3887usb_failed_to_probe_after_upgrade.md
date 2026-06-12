---
title: "isl3887usb failed to probe after upgrade"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by martinichka on 2010-05-23
I am very pleased with the upgrade to 10.4. However, since I upgraded the PC of my mom the wireless network device (USB) didn't work anymore. I found that the probe of the wireless device after firmware load failed.

With *lsusb* I see the device:
```
Bus 001 Device 004: ID 0cde:0015 Z-Com Zoom Wireless-G
```In */var/log/messages* I see:
```

May 23 08:40:46 ytsje-desktop kernel: [ 2609.256358] usb 1-4: USB disconnect, address 2
May 23 08:40:50 ytsje-desktop kernel: [ 2613.156301] usb 1-4: new high speed USB device using ehci_hcd and address 4
May 23 08:40:50 ytsje-desktop kernel: [ 2613.300705] usb 1-4: configuration #1 chosen from 1 choice
May 23 08:40:50 ytsje-desktop kernel: [ 2613.540076] usb 1-4: reset high speed USB device using ehci_hcd and address 4
May 23 08:40:50 ytsje-desktop kernel: [ 2613.677824] usb 1-4: firmware: requesting isl3887usb
May 23 08:40:50 ytsje-desktop kernel: [ 2613.695709] usb 1-4: firmware: requesting isl3887usb_bare
May 23 08:40:50 ytsje-desktop kernel: [ 2613.704001] p54usb: probe of 1-4:1.0 failed with error -2
May 23 08:40:50 ytsje-desktop kernel: [ 2613.704077] usbcore: registered new interface driver p54usb

```It's quite annoying because it's not my own computer. Anyone suggestions?

---

### Post by martinichka on 2010-05-23
I found a related bug, with solution (my post #13):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383?comments=all)

---

