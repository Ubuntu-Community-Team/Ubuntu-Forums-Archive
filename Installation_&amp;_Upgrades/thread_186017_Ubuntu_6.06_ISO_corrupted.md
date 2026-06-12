---
title: "Ubuntu 6.06 ISO corrupted?"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by istoyanov on 2006-06-01
I have just downloaded the Ubuntu 6.06 ISO (ubuntu-6.06-desktop-i386.iso md5sum OK!) and burnt it to several(!) CDs, but after Ubuntu gets "live", I have a series of very disturbing error messages in dmesg:
```

ubuntu@ubuntu:~$ less /var/log/messages | grep hdb
Jun  1 18:26:21 ubuntu kernel: [   32.039470]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Jun  1 18:26:21 ubuntu kernel: [   33.016276] hdb: CDU5211, ATAPI CD/DVD-ROM drive
Jun  1 18:26:21 ubuntu kernel: [   34.109871] hdb: ATAPI 52X CD-ROM drive, 120kB Cache, UDMA(33)
Jun  1 18:26:21 ubuntu kernel: [   41.193213] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:21 ubuntu kernel: [   41.193229] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jun  1 18:26:21 ubuntu kernel: [   41.193246] end_request: I/O error, dev hdb, sector 1429192
Jun  1 18:26:21 ubuntu kernel: [   46.240072] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:21 ubuntu kernel: [   46.240082] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jun  1 18:26:21 ubuntu kernel: [   46.240096] end_request: I/O error, dev hdb, sector 1429192
Jun  1 18:26:21 ubuntu kernel: [   51.051987] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:21 ubuntu kernel: [   51.051998] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jun  1 18:26:21 ubuntu kernel: [   51.052011] end_request: I/O error, dev hdb, sector 1429192
Jun  1 18:26:21 ubuntu kernel: [   55.747883] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:21 ubuntu kernel: [   55.747893] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jun  1 18:26:21 ubuntu kernel: [   55.747905] end_request: I/O error, dev hdb, sector 1429192
Jun  1 18:26:21 ubuntu kernel: [   60.685320] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:21 ubuntu kernel: [   60.685330] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jun  1 18:26:21 ubuntu kernel: [   60.685343] end_request: I/O error, dev hdb, sector 1429192
Jun  1 18:26:21 ubuntu kernel: [   65.711316] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:21 ubuntu kernel: [   65.711326] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jun  1 18:26:21 ubuntu kernel: [   65.711338] end_request: I/O error, dev hdb, sector 1429192
Jun  1 18:26:21 ubuntu kernel: [   65.838353] hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:21 ubuntu kernel: [   65.838363] hdb: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jun  1 18:26:21 ubuntu kernel: [   65.838375] end_request: I/O error, dev hdb, sector 1429184
Jun  1 18:26:21 ubuntu kernel: [   65.856502] hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:21 ubuntu kernel: [   65.856510] hdb: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jun  1 18:26:21 ubuntu kernel: [   65.856521] end_request: I/O error, dev hdb, sector 1429188
Jun  1 18:26:21 ubuntu kernel: [   65.892795] hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:21 ubuntu kernel: [   65.892804] hdb: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jun  1 18:26:21 ubuntu kernel: [   65.892815] end_request: I/O error, dev hdb, sector 1429184
Jun  1 18:26:21 ubuntu kernel: [   65.910929] hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:21 ubuntu kernel: [   65.910938] hdb: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jun  1 18:26:21 ubuntu kernel: [   65.910949] end_request: I/O error, dev hdb, sector 1429188
Jun  1 18:26:42 ubuntu kernel: [  263.330042] hdb: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
Jun  1 18:26:42 ubuntu kernel: [  263.330062] hdb: drive_cmd: error=0x04 { AbortedCommand }

```

Note, that **hdb is my CD-ROM drive** from where the live CD runs (more or less successfully?) at the moment, and I am now posting from it as well!

I have tried to run all the burnt CDs on another machine and I've got the same error messages for the corresponding CD-ROM drive (hdc, in the second case).

Has someone else experienced such strange behaviour?

Now I'm really reluctant to installing Drapper Drake on either of these machines, assuming that these messages are hinting at severe hardware incompatibilities. Am I missing some boot options? Or is the released ISO somehow corrupt? :(

Any hint or advice would be greatly appreciated!

Cheers!!!

---

### Post by meng on 2006-06-01
EDIT: Irrelevant. Sorry.

---

