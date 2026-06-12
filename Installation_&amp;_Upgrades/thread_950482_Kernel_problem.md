---
title: "Kernel problem"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by provolone25 on 2008-10-17
Hi i updated some days ago to ubuntu intrepid all is k except the boot; when i load the kernel i get this message:
```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT ! /dev/disk/by-uuid/d2a9.............. does not exist 
```
and go to console; then the kernel load the driver for the hd and i can load the system typing exit in the console.
But i dont understand why the system loads the module after trying to boot the system. Some1 can help me? Thanks

---

### Post by Pumalite on 2008-10-17
Post:
blkid

---

### Post by provolone25 on 2008-10-17
The id is correct i already checked it :)

---

### Post by Pumalite on 2008-10-17
What about /swap?

---

### Post by Ayuthia on 2008-10-17
What does ls -l /dev/disk/by-uuid show?

---

### Post by provolone25 on 2008-10-17
It show the correct id i tryed all it seems that kernel make boot then load the driver; i see it from kernel message during boot

---

### Post by provolone25 on 2008-10-18
```
Oct 18 08:18:30 xeon kernel: [   33.832634] ata1.00: 120103200 sectors, multi 16: LBA 
Oct 18 08:18:30 xeon kernel: [   33.848391] ata1.00: configured for UDMA/100
Oct 18 08:18:30 xeon kernel: [   34.012301] ata2.00: ATAPI: DVD DUAL GO-W0404A, VER 0051, max UDMA/66
Oct 18 08:18:30 xeon kernel: [   34.028236] ata2.00: configured for UDMA/66
Oct 18 08:18:30 xeon kernel: [   34.028340] scsi: waiting for bus probes to complete ...
Oct 18 08:18:30 xeon kernel: [   34.924179] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0031004bb3]
```
Here go to shell returing error then

```
Oct 18 08:18:30 xeon kernel: [   37.447012] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6Y060L0   YAR4 PQ: 0 ANSI: 5
Oct 18 08:18:30 xeon kernel: [   37.454042] sd 3:0:0:0: [sdb] 120103200 512-byte hardware sectors (61493 MB)
Oct 18 08:18:30 xeon kernel: [   37.460428] sd 3:0:0:0: [sdb] Write Protect is off
Oct 18 08:18:30 xeon kernel: [   37.466725] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct 18 08:18:30 xeon kernel: [   37.466765] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 18 08:18:30 xeon kernel: [   37.473307] sd 3:0:0:0: [sdb] 120103200 512-byte hardware sectors (61493 MB)
Oct 18 08:18:30 xeon kernel: [   37.479843] sd 3:0:0:0: [sdb] Write Protect is off
Oct 18 08:18:30 xeon kernel: [   37.486294] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct 18 08:18:30 xeon kernel: [   37.486331] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 18 08:18:30 xeon kernel: [   37.492844]  sdb: sdb1 sdb2 sdb3 sdb4
Oct 18 08:18:30 xeon kernel: [   37.518373] sd 3:0:0:0: [sdb] Attached SCSI disk
Oct 18 08:18:30 xeon kernel: [   37.525039] sd 3:0:0:0: Attached scsi generic sg1 type 0
Oct 18 08:18:30 xeon kernel: [   37.532339] scsi 4:0:0:0: CD-ROM            DVD DUAL GO-W0404A        0051 PQ: 0 ANSI: 5
Oct 18 08:18:30 xeon kernel: [   37.539809] scsi 4:0:0:0: Attached scsi generic sg2 type 5
Oct 18 08:18:30 xeon kernel: [   37.594164] Driver 'sr' needs updating - please use bus_type methods
Oct 18 08:18:30 xeon kernel: [   37.604461] sr0: scsi3-mmc drive: 1x/40x writer cd/rw xa/form2 cdda tray
Oct 18 08:18:30 xeon kernel: [   37.610945] Uniform CD-ROM driver Revision: 3.20
Oct 18 08:18:30 xeon kernel: [   37.618792] sr 4:0:0:0: Attached scsi CD-ROM sr0
```

load the driver; notice the second from 37 to 69;

```
Oct 18 08:18:30 xeon kernel: [   69.897416] PM: Starting manual resume from disk
Oct 18 08:18:30 xeon kernel: [   69.903687] PM: Resume from partition 8:18
Oct 18 08:18:30 xeon kernel: [   69.903690] PM: Checking hibernation image.
Oct 18 08:18:30 xeon kernel: [   69.903895] PM: Resume from disk failed.
Oct 18 08:18:30 xeon kernel: [   69.951713] kjournald starting.  Commit interval 5 seconds
Oct 18 08:18:30 xeon kernel: [   69.958027] EXT3-fs: mounted filesystem with ordered data mode.
```
Some1 can help me? :)

---

