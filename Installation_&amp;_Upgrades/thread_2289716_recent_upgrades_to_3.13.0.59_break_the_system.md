---
title: "recent upgrades to 3.13.0.59 break the system"
date: 2015-08-06
forum: Installation &amp; Upgrades
---

### Post by Serban_Maerean on 2015-08-06
Maybe the title is not really meaningful, but don't know what generates this problem.  After updating the system to kernel 3.13.0.59, I noticed that the network connection drops soon after restarting the system.  The router simply sees is as "off", but every other command shows the adapter working fine.

Looking at the kernel messages, I noticed the following:

[   36.451427] type=1400 audit(1438868166.228:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3391 comm="apparmor_parser"
[   36.451433] type=1400 audit(1438868166.228:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3391 comm="apparmor_parser"
[   36.451879] type=1400 audit(1438868166.228:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3391 comm="apparmor_parser"
[   36.986805] 2:3:1: cannot get freq at ep 0x82
[   41.986540] 2:3:1: cannot get freq at ep 0x82
[   42.022439] AMD-Vi: Event logged [IO_PAGE_FAULT device=04:00.0 domain=0x0018 address=0x000000000002a000 flags=0x0000]
[   42.055391] xhci_hcd 0000:04:00.0: WARNING: Host System Error
[   42.087222] xhci_hcd 0000:04:00.0: Host not halted after 16000 microseconds.
[   52.033830] xhci_hcd 0000:04:00.0: xHCI host not responding to stop endpoint command.
[   52.033839] xhci_hcd 0000:04:00.0: Assuming host is dying, halting host.
[   52.065665] xhci_hcd 0000:04:00.0: Host not halted after 16000 microseconds.
[   52.065679] xhci_hcd 0000:04:00.0: Non-responsive xHCI host is not halting.
[   52.065680] xhci_hcd 0000:04:00.0: Completing active URBs anyway.
[   52.065701] xhci_hcd 0000:04:00.0: HC died; cleaning up
[   52.065802] usb 10-1: USB disconnect, device number 2

When these messages show up, the network adapter stops working.  Apparently, an issue w/the xhci_hcd driver?!?

It works well w/3.13.0.57 and it's still broken w/3.13.0.61.  Any suggestions?

Thanks much.

---

### Post by Serban_Maerean on 2015-08-06
I found this problem being reported with bug 1447053 ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1447053](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1447053)).  The bug reports the problem manifests with kernel 3.13.0.49, but I didn't see it at that level.  The first time I saw it was in 3.13.0.59.  No changes to the system hardware since kernel level 3.13.0.57, which doesn't have this problem.

I have the following network adapter:
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.

and I am using the r8169 device driver w/the 3.13.0.57 (the kernel version that works fine.)

W/the kernel version that doesn't work (3.13.0.59), I updated the device driver to r8168 (apparently the version listed in the product name) and I see no difference, i.e. same failure.  Once the AMD-Vi IO_PAGE_FAULT message shows up in dmesg, the network adapter stops working.

Any solution to this problem?

Thanks much.

---

