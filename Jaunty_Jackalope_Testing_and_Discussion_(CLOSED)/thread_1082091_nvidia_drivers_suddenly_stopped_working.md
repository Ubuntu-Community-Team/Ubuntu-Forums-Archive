---
title: "nvidia drivers suddenly stopped working"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by KhaaL on 2009-02-27
Hi!

I had my nvidia drivers working earlier today but now they decided suddenly to stop working without me modifying xorg.conf or anything... :? i'm not getting any graphical acceleration at all. nvidia-settings does complain on the driver not running. i got 180.29 drivers from deb [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main

Here's the output of dmesg | grep -i nv
```

[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  modified: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    1.117620] sata_nv 0000:00:0e.0: version 3.5
[    1.118015] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.118018] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.118074] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.118208] scsi0 : sata_nv
[    1.118349] scsi1 : sata_nv
[    2.983589] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    2.983591] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    2.983632] sata_nv 0000:00:0f.0: setting latency timer to 64
[    2.983772] scsi2 : sata_nv
[    2.983922] scsi3 : sata_nv
[    5.325233] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    5.650422] nv_probe: set workaround bit for reversed mac addr
[   10.809476] nvidia: module license 'NVIDIA' taints kernel.
[   11.446321] nvidia 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   11.446334] nvidia 0000:02:00.0: setting latency timer to 64
[   11.446971] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.29  Wed Feb  4 23:39:47 PST 2009

```

---

### Post by taavikko on 2009-02-27
Like I said in the other post, there were X.org update earlier today, did you do that one and restarted?

---

### Post by KhaaL on 2009-02-27
Thank you for the quick reply, yes i did. Should I wait for the next ubuntu update or the next update from the PPA? (I really dont have an understanding of how drivers, kernel and modules work toghether...)

From my apt log:
*Setting up xorg (1:7.4~5ubuntu13) ...*

---

### Post by Nullack on 2009-02-27
Khaal have a look at the wiki on debugging X problems, links in the contributing to jaunty post

---

### Post by KhaaL on 2009-02-27
I just found out that there was an API mismatch that was the cause between 180.29 and 180.35 drivers. weird, since the nvidia-glx-180 showed version 180.29 in apt... I'll dig more into this...

---

