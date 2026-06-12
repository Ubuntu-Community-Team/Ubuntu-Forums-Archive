---
title: "USB drives not loaded when including entry for ndiswrapper in /etc/modules"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by goa-mark on 2010-03-27
I am running Ubuntu 10.04 beta 1. After following the instructions for using ndiswrapper (at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)), I added an entry for ndiswrapper into /etc/modules. After doing this, USB drives fail to be loaded. My USB keyboard and mouse still work, and the drives work in my other machines.

Here is the output from /var/log/messages when it fails to load (the last line is from me manually unplugging the device):

```
Mar 27 17:43:42 sikkim kernel: [  696.172053] usb 1-1: new high speed USB device using ehci_hcd and address 12
Mar 27 17:43:42 sikkim kernel: [  696.305899] usb 1-1: configuration #1 chosen from 1 choice
Mar 27 17:44:48 sikkim kernel: [  761.379113] usb 1-1: USB disconnect, address 12
```


When it works, it looks like this (it's a different machine, but the output is the same):
```
Mar 27 18:18:17 goa kernel: [23473.988107] usb 1-7: new high speed USB device using ehci_hcd and address 4
Mar 27 18:18:17 goa kernel: [23474.125704] usb 1-7: configuration #1 chosen from 1 choice
Mar 27 18:18:17 goa kernel: [23474.126197] scsi3 : SCSI emulation for USB Mass Storage devices
Mar 27 18:18:22 goa kernel: [23479.142332] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.1  PQ: 0 ANSI: 2
Mar 27 18:18:22 goa kernel: [23479.143177] sd 3:0:0:0: Attached scsi generic sg2 type 0
Mar 27 18:18:22 goa kernel: [23479.158807] sd 3:0:0:0: [sdb] 501759 512-byte logical blocks: (256 MB/244 MiB)
Mar 27 18:18:22 goa kernel: [23479.160137] sd 3:0:0:0: [sdb] Write Protect is off
Mar 27 18:18:22 goa kernel: [23479.165276]  sdb: sdb1
Mar 27 18:18:22 goa kernel: [23479.170874] sd 3:0:0:0: [sdb] Attached SCSI removable disk

```

Looking through /var/log/messages, I did find one thing curious. When I have ndiswrapper in /etc/modules, I get a line in the log right after loading ndiswrapper:

```
Mar 27 18:05:34 sikkim kernel: [   16.762898] usbcore: registered new interface driver ndiswrapper
```

I am wondering if somehow ndiswrapper is interfering with the behavior of how usb devices are being handled. When I remove ndiswrapper from /etc/modules and reboot, my usb devices are detected and mounted correctly again.

Unfortunately I don't have an official-release version of Ubuntu to test this on, so I don't know if it's new to 10.04 or not.

Mark

---

