---
title: "Lucid can't mount Archos 3 Vision MP3 (USB)"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Fred2a on 2010-03-13
Hi Folks,

My Archos 3 mounts just fine as a mass storage device under Jaunty and Karmic.

However when I plug it in under Lucid I get the following:

```

[  262.872160] usb 1-2: new high speed USB device using ehci_hcd and address 3
[  263.005450] usb 1-2: configuration #1 chosen from 1 choice
[  263.017154] scsi3 : SCSI emulation for USB Mass Storage devices
[  263.018839] usb-storage: device found at 3
[  263.018854] usb-storage: waiting for device to settle before scanning
[  268.016467] usb-storage: device scan complete
[  268.017192] scsi 3:0:0:0: Direct-Access              Archos3          1.00 PQ: 0 ANSI: 0
[  268.021992] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  268.024763] sd 3:0:0:0: [sdc] 16015360 512-byte logical blocks: (8.19 GB/7.63 GiB)
[  268.024785] sd 3:0:0:0: [sdc] Assuming Write Enabled
[  268.024800] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  268.040787] sd 3:0:0:0: [sdc] Assuming Write Enabled
[  268.040797] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  268.040811]  sdc:
[  268.046134] sd 3:0:0:0: [sdc] Assuming Write Enabled
[  268.046144] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  268.046156] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[  275.928170] usb 1-2: reset high speed USB device using ehci_hcd and address 3
[  283.872532] usb 1-2: USB disconnect, address 3
[  283.873433] sd 3:0:0:0: Device offlined - not ready after error recovery

```I've checked this and this problem is present on all the kernels so far:
2.6.32-14
2.6.32-15
2.6.32-16

Anyone else having bother mounting mass storage devices in Lucid?

Any ideas what I should file a bug against?

---

### Post by Fred2a on 2010-03-21
bump

---

### Post by tadcan on 2010-04-03
I just bought the same model of archos. It wont mount for me either.

---

### Post by feralert on 2010-04-12
Same thing here, cant mount it on lucyd. It seems the device doesnt get recognised by the kernel since it doesnt even appear on a lspci. 

Is this a kernel or a ubuntu issue?? If i have the time will try the latest kernel from kernel.org and see what happens.

Regards.

---

