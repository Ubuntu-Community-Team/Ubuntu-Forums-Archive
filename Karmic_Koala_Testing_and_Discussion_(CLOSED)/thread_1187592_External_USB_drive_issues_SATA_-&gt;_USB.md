---
title: "External USB drive issues? SATA -&gt; USB"
date: 2009-06-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cowbud on 2009-06-14
I recently started running in to issues where my external SATA -> USB drive no longer initializes correctly in Koala. It works fine in Windows and in other variants of linux (Even previous version of Ubuntu) so I am suspicious of recent updates. This happens with kernels older than 2.6.30 as well. 

Before I file a bug i wanted to ask here.

For what it is worth the enclosure is a NexStar CX from Vantec

Is anyone else seeing similar issues?

Dmesg output:

> 
 386.064023] usb 1-4: new high speed USB device using ehci_hcd and address 8
[  386.213004] usb 1-4: configuration #1 chosen from 1 choice
[  386.232999] scsi9 : SCSI emulation for USB Mass Storage devices
[  386.233164] usb-storage: device found at 8
[  386.233167] usb-storage: waiting for device to settle before scanning
[  391.232304] usb-storage: device scan complete
[  391.232856] scsi 9:0:0:0: Direct-Access     Maxtor 7 H500F0                PQ: 0 ANSI: 2 CCS
[  391.233361] sd 9:0:0:0: Attached scsi generic sg6 type 0
[  391.251664] sd 9:0:0:0: [sdf] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[  391.252491] sd 9:0:0:0: [sdf] Write Protect is off
[  391.252496] sd 9:0:0:0: [sdf] Mode Sense: 34 00 00 00
[  391.252499] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[  391.253959] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[  391.253964]  sdf: sdf1
[  391.272447] sd 9:0:0:0: [sdf] Attached SCSI disk
[  399.100023] usb 1-4: reset high speed USB device using ehci_hcd and address 8
[  399.224032] usb 1-4: device descriptor read/64, error -71
[  399.452025] usb 1-4: device descriptor read/64, error -71
[  399.668022] usb 1-4: reset high speed USB device using ehci_hcd and address 8
[  399.792023] usb 1-4: device descriptor read/64, error -71
[  400.020026] usb 1-4: device descriptor read/64, error -71
[  400.236028] usb 1-4: reset high speed USB device using ehci_hcd and address 8
[  400.652029] usb 1-4: device not accepting address 8, error -71
[  400.764022] usb 1-4: reset high speed USB device using ehci_hcd and address 8
[  401.176019] usb 1-4: device not accepting address 8, error -71
[  401.176058] usb 1-4: USB disconnect, address 8
[  401.176995] scsi 9:0:0:0: Device offlined - not ready after error recovery
[  401.288015] usb 1-4: new high speed USB device using ehci_hcd and address 9
[  401.417078] usb 1-4: device descriptor read/64, error -71
[  401.644033] usb 1-4: device descriptor read/64, error -71
[  401.860128] usb 1-4: new high speed USB device using ehci_hcd and address 10
[  401.984066] usb 1-4: device descriptor read/64, error -71
[  402.212021] usb 1-4: device descriptor read/64, error -71
[  402.428027] usb 1-4: new high speed USB device using ehci_hcd and address 11
[  402.836017] usb 1-4: device not accepting address 11, error -71
[  402.948538] usb 1-4: new high speed USB device using ehci_hcd and address 12
[  403.364016] usb 1-4: device not accepting address 12, error -71
[  403.364035] hub 1-0:1.0: unable to enumerate USB device on port 4
[  403.632019] usb 3-2: new full speed USB device using uhci_hcd and address 2
[  403.752047] usb 3-2: device descriptor read/64, error -71
[  403.976092] usb 3-2: device descriptor read/64, error -71
[  404.192026] usb 3-2: new full speed USB device using uhci_hcd and address 3
[  404.313487] usb 3-2: device descriptor read/64, error -71
[  404.540028] usb 3-2: device descriptor read/64, error -71
[  404.756019] usb 3-2: new full speed USB device using uhci_hcd and address 4
[  405.164016] usb 3-2: device not accepting address 4, error -71
[  405.276046] usb 3-2: new full speed USB device using uhci_hcd and address 5
[  405.685586] usb 3-2: device not accepting address 5, error -71
[  405.685618] hub 3-0:1.0: unable to enumerate USB device on port 2



---

### Post by Gourgi on 2009-06-14
sounds like a regression to me
you better file a bug against linux 
```
ubuntu-bug linux
``` 
and describe the regression

---

### Post by cowbud on 2009-06-15
Thanks for the sanity check bug filed:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/387161](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/387161)

---

### Post by ranch hand on 2009-06-15
I have A1-32 on an internal HDD and A2-64 on a NexStar MX (dual).  I have no trouble with the external at all on any of my OSs.

The Vantec external is 1 of 2 externals, the other is a generic (single) and i have no trouble with it either.

---

### Post by taavikko on 2009-06-16
> **ranch hand said:**
> I have A1-32 on an internal HDD and A2-64 on a NexStar MX (dual).

If those installations are up-to-date, they're no longer A{1,2}
version number is just a snapshot of the repositories at that time.

Cause frequently applying updates, you'll eventually have the official release version. Hence no need to refer them as Alpha*.

---

### Post by ranch hand on 2009-06-16
> **taavikko said:**
> If those installations are up-to-date, they're no longer A{1,2}
version number is just a snapshot of the repositories at that time.

Cause frequently applying updates, you'll eventually have the official release version. Hence no need to refer them as Alpha*.

This is true.  I am going to have to install grub2 on the A1-32 partition though if i want them to be the same.  I think I will wait until I know a little more about messing with grub2.

---

### Post by taavikko on 2009-06-16
> **ranch hand said:**
> This is true.  I am going to have to install grub2 on the A1-32 partition though if i want them to be the same.  I think I will wait until I know a little more about messing with grub2.

no you don't. Grub2 will be default when installed via Alpha2->
Previous way is stuck with older grub. (upgraded from Jaunty or installing daily-live/alpha1)

Grub2: [https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview](https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview)

---

