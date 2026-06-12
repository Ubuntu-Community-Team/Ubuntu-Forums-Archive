---
title: "Gen 1 Ipod Touch Support"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by a.walker on 2010-03-29
I connected my 1st Gen iPod touch to my computer and Lucid recognized and mounted it. The problem is that it keeps mounting and unmounting it. (It's only a small annoyance, but one that I would like to resolve.)

The following is an excerpt from my log file:

```

Mar 29 20:52:43 andy-desktop kernel: [   73.948018] usb 1-1: new high speed USB device using ehci_hcd and address 3
Mar 29 20:52:44 andy-desktop kernel: [   74.085189] usb 1-1: configuration #1 chosen from 3 choices
Mar 29 20:52:55 andy-desktop kernel: [   85.162309] usb 1-1: USB disconnect, address 3
Mar 29 20:52:55 andy-desktop kernel: [   85.436024] usb 1-1: new high speed USB device using ehci_hcd and address 4
Mar 29 20:52:55 andy-desktop kernel: [   85.573499] usb 1-1: configuration #1 chosen from 3 choices
Mar 29 20:53:16 andy-desktop kernel: [  106.378120] usb 1-1: USB disconnect, address 4
Mar 29 20:53:16 andy-desktop kernel: [  106.620046] usb 1-1: new high speed USB device using ehci_hcd and address 5
Mar 29 20:53:16 andy-desktop kernel: [  106.757224] usb 1-1: configuration #1 chosen from 3 choices
Mar 29 20:54:46 andy-desktop kernel: [  196.709173] usb 1-1: USB disconnect, address 5
Mar 29 20:54:47 andy-desktop kernel: [  196.980029] usb 1-1: new high speed USB device using ehci_hcd and address 6
Mar 29 20:54:47 andy-desktop kernel: [  197.119100] usb 1-1: configuration #1 chosen from 3 choices
Mar 29 20:56:45 andy-desktop kernel: [  315.933068] usb 1-1: USB disconnect, address 6
Mar 29 20:56:46 andy-desktop kernel: [  316.176038] usb 1-1: new high speed USB device using ehci_hcd and address 7
Mar 29 20:56:46 andy-desktop kernel: [  316.313028] usb 1-1: configuration #1 chosen from 3 choices
Mar 29 20:56:53 andy-desktop kernel: [  323.108968] usb 1-1: USB disconnect, address 7
Mar 29 20:56:53 andy-desktop kernel: [  323.380039] usb 1-1: new high speed USB device using ehci_hcd and address 8
Mar 29 20:56:53 andy-desktop kernel: [  323.517668] usb 1-1: configuration #1 chosen from 3 choices
Mar 29 21:01:06 andy-desktop kernel: [  576.162331] usb 1-1: USB disconnect, address 8
Mar 29 21:01:06 andy-desktop kernel: [  576.437058] usb 1-1: new high speed USB device using ehci_hcd and address 9
Mar 29 21:01:06 andy-desktop kernel: [  576.573225] usb 1-1: configuration #1 chosen from 3 choices

```

Any thoughts on this matter? Is this a known issue and are there workarounds?

---

