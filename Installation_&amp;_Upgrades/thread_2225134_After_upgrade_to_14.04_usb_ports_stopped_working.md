---
title: "After upgrade to 14.04 usb ports stopped working"
date: 2014-05-20
forum: Installation &amp; Upgrades
---

### Post by ElDulce on 2014-05-20
I'm not sure where the problem is. I've got Xubuntu installed on an Asus K-series. Everything worked fine with 13.


lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and from dmesg


[   17.718741] usb 2-4: new full-speed USB device number 5 using xhci_hcd
[   22.722845] WARNING: CPU: 0 PID: 0 at /build/buildd/linux-3.13.0/drivers/usb/host/xhci-ring.c:1572 handle_cmd_completion+0xd70/0xd80()
[   28.135174] usb 2-4: device not accepting address 5, error -108
[   33.139262] xhci_hcd 0000:00:14.0: Timeout while waiting for a slot
[   33.139271] xhci_hcd 0000:00:14.0: Abort the command ring, but the xHCI is dead.
[   38.143280] xhci_hcd 0000:00:14.0: Timeout while waiting for a slot
[   38.143286] xhci_hcd 0000:00:14.0: Abort the command ring, but the xHCI is dead.
[   43.144834] xhci_hcd 0000:00:14.0: Timeout while waiting for a slot
[   43.144839] xhci_hcd 0000:00:14.0: Abort the command ring, but the xHCI is dead.
[   43.144860] usb 2-5: USB disconnect, device number 3
[   43.177038] usb 2-8: USB disconnect, device number 4


Thanks for having a look at this.

---

### Post by ElDulce on 2014-05-21
Bump

---

