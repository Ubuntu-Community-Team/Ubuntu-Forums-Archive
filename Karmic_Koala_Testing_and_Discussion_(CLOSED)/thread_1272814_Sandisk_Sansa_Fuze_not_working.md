---
title: "Sandisk Sansa Fuze not working"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by HankB on 2009-09-22
My Sansa Fuze does not connect on my Eee PC 901 when I'm running Karmic. It works fine when running Jaunty. The Fuze is set to MSC mode.

Results from dmesg include:
```

[  648.848196] usb 1-2: new high speed USB device using ehci_hcd and address 5
[  651.996415] hub 1-0:1.0: unable to enumerate USB device on port 2
[  652.244167] usb 1-2: new high speed USB device using ehci_hcd and address 6
[  652.390231] usb 1-2: configuration #1 chosen from 1 choice
[  652.415501] scsi3 : SCSI emulation for USB Mass Storage devices
[  652.415919] usb-storage: device found at 6
[  652.415927] usb-storage: waiting for device to settle before scanning
[  657.412788] usb-storage: device scan complete
[  678.112214] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[  678.724217] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[  684.240171] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[  699.352186] usb 1-2: device descriptor read/64, error -110
[  709.744163] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 266
[  714.568197] usb 1-2: device descriptor read/64, error -110
[  714.784194] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[  729.896162] usb 1-2: device descriptor read/64, error -110

```

lsusb does not seem to see this device and takes a l-o-n-g time to report this.

This also seems to put the Sansa Fuze into a bad state as since disconnected, it just sits there and I have to reset it by holding the off button.

My Sansa e280 does mount but it takes a long time. dmesg reports:
```
[ 1752.804498] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 1753.188205] usb 1-2: new high speed USB device using ehci_hcd and address 12
[ 1753.340100] usb 1-2: configuration #1 chosen from 1 choice
[ 1753.342177] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1753.342864] usb-storage: device found at 12
[ 1753.342879] usb-storage: waiting for device to settle before scanning
[ 1758.342762] usb-storage: device scan complete
[ 1758.344932] scsi 4:0:0:0: Direct-Access     Rockbox  Internal Storage 0.00 PQ: 0 ANSI: 4
[ 1758.348316] scsi 4:0:0:1: Direct-Access     Rockbox  SD Card Slot     0.00 PQ: 0 ANSI: 4
[ 1758.350295] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 1758.350983] sd 4:0:0:1: Attached scsi generic sg4 type 0
[ 1758.364201] sd 4:0:0:0: [sdd] 15708160 512-byte logical blocks: (8.04 GB/7.49 GiB)
[ 1758.369124] sd 4:0:0:0: [sdd] Write Protect is off
[ 1758.369139] sd 4:0:0:0: [sdd] Mode Sense: 0b 00 00 08
[ 1758.369147] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[ 1758.374569] sd 4:0:0:1: [sde] Attached SCSI removable disk
[ 1758.388577] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[ 1758.388596]  sdd: sdd1 sdd2
[ 1758.418343] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[ 1758.418358] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[ 1789.743729] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 418

```

It mounts it as /media/49E1-3D54 which seems a bit odd.

Other USB devices (flash drives on hand) seem to work OK.

Report a bug?

---

### Post by motang on 2009-10-05
I get something similar, I can still get and put stuff on to my Fuze but it mounts as 0123-4567 so I had to change a few things with gPodcatcher and other software. It does take sometime to mount but not as long as you descibed it. Also put podcast on to it is freaking slow as week and half ago with Jaunty it was lighting fast.

---

### Post by cytmtn on 2009-10-08
I'm in the same boat.

Upgraded to karmic and now it doesn't mount at all. Have you filed a bug report?

---

### Post by HankB on 2009-10-08
> **cytmtn said:**
> I'm in the same boat.

Upgraded to karmic and now it doesn't mount at all. Have you filed a bug report?
No. I cast this out to see if anyone had the same problem and in the mean time, the problem has cleared up for me.

The Fuze still mounts with unusual names but doesn't get locked up and seems to mount reliably.

-hank

---

