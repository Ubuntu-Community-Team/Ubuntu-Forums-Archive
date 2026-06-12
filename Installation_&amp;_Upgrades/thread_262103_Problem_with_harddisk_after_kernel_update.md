---
title: "Problem with harddisk after kernel update"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by math on 2006-09-21
I compiled the new 2.6.18 and installed it. After that i cant mount one of my harddisks. The other harddisk on the same sata adapter works fine.
The hd is recognized properly during boot (look for HDS722525VLSA80):
```
Sep 21 08:35:22 localhost kernel: [   44.796981] scsi4 : sata_sil
Sep 21 08:35:22 localhost kernel: [   45.263979] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 21 08:35:22 localhost kernel: [   45.265033] ata5.00: ATA-7, max UDMA/133, 625134827 sectors: LBA48 NCQ (depth 0/32)
Sep 21 08:35:22 localhost kernel: [   45.265077] ata5.00: ata5: dev 0 multi count 16
Sep 21 08:35:22 localhost kernel: [   45.266315] ata5.00: configured for UDMA/100
Sep 21 08:35:22 localhost kernel: [   45.266355] scsi5 : sata_sil
Sep 21 08:35:22 localhost kernel: [   45.731404] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 21 08:35:22 localhost kernel: [   45.732940] ata6.00: ATA-6, max UDMA/100, 488397168 sectors: LBA48 
Sep 21 08:35:22 localhost kernel: [   45.732976] ata6.00: ata6: dev 0 multi count 16
Sep 21 08:35:22 localhost kernel: [   45.734821] ata6.00: configured for UDMA/100
Sep 21 08:35:22 localhost kernel: [   45.734925]   Vendor: ATA       Model: ST3320620AS       Rev: 3.AA
Sep 21 08:35:22 localhost kernel: [   45.735654]   Type:   Direct-Access                      ANSI SCSI revision: 05
Sep 21 08:35:22 localhost kernel: [   45.735939]   Vendor: ATA       Model: HDS722525VLSA80   Rev: V36O
Sep 21 08:35:22 localhost kernel: [   45.736663]   Type:   Direct-Access                      ANSI SCSI revision: 05
Sep 21 08:35:22 localhost kernel: [   45.748374] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
Sep 21 08:35:22 localhost kernel: [   45.748421] sda: Write Protect is off
Sep 21 08:35:22 localhost kernel: [   45.748454] sda: Mode Sense: 00 3a 00 00
Sep 21 08:35:22 localhost kernel: [   45.748464] SCSI device sda: drive cache: write back
Sep 21 08:35:22 localhost kernel: [   45.748539] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
Sep 21 08:35:22 localhost kernel: [   45.748579] sda: Write Protect is off
Sep 21 08:35:22 localhost kernel: [   45.748612] sda: Mode Sense: 00 3a 00 00
Sep 21 08:35:22 localhost kernel: [   45.748620] SCSI device sda: drive cache: write back
Sep 21 08:35:22 localhost kernel: [   45.748655]  sda: sda1 sda2 sda4
Sep 21 08:35:22 localhost kernel: [   45.783648] sd 1:0:0:0: Attached scsi disk sda
Sep 21 08:35:22 localhost kernel: [   45.787143] SCSI device sdb: 625134827 512-byte hdwr sectors (320069 MB)
Sep 21 08:35:22 localhost kernel: [   45.787321] sdb: Write Protect is off
Sep 21 08:35:22 localhost kernel: [   45.787354] sdb: Mode Sense: 00 3a 00 00
Sep 21 08:35:22 localhost kernel: [   45.791325] SCSI device sdb: drive cache: write back
Sep 21 08:35:22 localhost kernel: [   45.795314] SCSI device sdb: 625134827 512-byte hdwr sectors (320069 MB)
Sep 21 08:35:22 localhost kernel: [   45.795908] sdb: Write Protect is off
Sep 21 08:35:22 localhost kernel: [   45.795943] sdb: Mode Sense: 00 3a 00 00
Sep 21 08:35:22 localhost kernel: [   45.795955] SCSI device sdb: drive cache: write back
Sep 21 08:35:22 localhost kernel: [   45.795992]  sdb: sdb1 sdb2
Sep 21 08:35:22 localhost kernel: [   45.837019] sd 4:0:0:0: Attached scsi disk sdb
Sep 21 08:35:22 localhost kernel: [   45.839270] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Sep 21 08:35:22 localhost kernel: [   45.840675] sdc: Write Protect is off
Sep 21 08:35:22 localhost kernel: [   45.840712] sdc: Mode Sense: 00 3a 00 00
Sep 21 08:35:22 localhost kernel: [   45.842757] SCSI device sdc: drive cache: write back
Sep 21 08:35:22 localhost kernel: [   45.843253] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Sep 21 08:35:22 localhost kernel: [   45.846449] sdc: Write Protect is off
Sep 21 08:35:22 localhost kernel: [   45.846486] sdc: Mode Sense: 00 3a 00 00
Sep 21 08:35:22 localhost kernel: [   45.846500] SCSI device sdc: drive cache: write back
Sep 21 08:35:22 localhost kernel: [   45.846548]  sdc: sdc1
Sep 21 08:35:22 localhost kernel: [   45.861860] sd 5:0:0:0: Attached scsi disk sdc
```
if i try to mount it manually:
```
mount: /dev/sdc1 already mounted or /media/sdc1 busy
```

I hope someone can help me.

---

### Post by tworkemon on 2006-09-23
You need to patch your kernel.
```
sudo apt-get install kernel-patch-evms
```
```
sudo cp /usr/src/kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch.gz /usr/src/your_kernel
```
```
sudo gzip -d 2.6-bd-claim.patch.gz
```
```
sudo cat 2.6-bd-claim.patch | patch -p1
```

After you do that rerun your kernel configuration.
```
sudo cp /boot/config-`uname -r` .config && sudo make xconfig
```
and continue the kernel upgrade process.

---

