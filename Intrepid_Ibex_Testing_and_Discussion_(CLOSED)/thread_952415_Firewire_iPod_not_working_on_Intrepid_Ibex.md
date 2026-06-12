---
title: "Firewire iPod not working on Intrepid Ibex"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by felixleong on 2008-10-19
I'm currently having some problems with my **3rd generation iPod** with **Intrepid Ibex** (kernel version: 2.6.27-7), which it detects but unable to be mounted.

A quick summary of dmesg (complete dmesg attached below):
```
[    3.527161] ohci1394 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.580011] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[dffff000-dffff7ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[    3.584984] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes

*** SNIPPED ***

[  155.140067] ieee1394: The root node is not cycle master capable; selecting a 
new root node and resetting...
[  155.418754] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000a270002759ee2]
[  155.420139] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[  155.424178] scsi2 : SBP-2 IEEE-1394
[  156.607467] ieee1394: sbp2: Logged into SBP-2 device
[  156.608593] ieee1394: sbp2: Node 0-00:1023: Max speed [S100] - Max payload [5
12]
[  156.612113] scsi 2:0:0:0: Direct-Access-RBC Apple    iPod             1.53 PQ
: 0 ANSI: 2
[  158.493733] sd 2:0:0:0: [sdc] Spinning up disk....ready
[  159.498084] sd 2:0:0:0: [sdc] 29297520 512-byte hardware sectors (15000 MB)
[  159.501098] sd 2:0:0:0: [sdc] Test WP failed, assume Write Enabled
[  159.503075] sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doe
sn't support DPO or FUA
[  159.508318] sd 2:0:0:0: [sdc] 29297520 512-byte hardware sectors (15000 MB)
[  159.511737] sd 2:0:0:0: [sdc] Test WP failed, assume Write Enabled
[  159.514685] sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  159.516044]  sdc: sdc1 sdc2
[  159.537291] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[  159.538490] sd 2:0:0:0: Attached scsi generic sg3 type 14
[  159.665985] end_request: I/O error, dev sdc, sector 104
[  159.666003] Buffer I/O error on device sdc, logical block 13
[  159.666010] Buffer I/O error on device sdc, logical block 14
[  159.666014] Buffer I/O error on device sdc, logical block 15
[  159.666018] Buffer I/O error on device sdc, logical block 16
[  159.666021] Buffer I/O error on device sdc, logical block 17
[  159.666025] Buffer I/O error on device sdc, logical block 18
[  159.666028] Buffer I/O error on device sdc, logical block 19
[  159.666031] Buffer I/O error on device sdc, logical block 20
[  159.666034] Buffer I/O error on device sdc, logical block 21
[  159.666038] Buffer I/O error on device sdc, logical block 22
[  159.666759] end_request: I/O error, dev sdc, sector 104
[  159.668096] end_request: I/O error, dev sdc, sector 104
[  159.669044] end_request: I/O error, dev sdc, sector 104
[  159.669866] end_request: I/O error, dev sdc, sector 104
[  159.703054] end_request: I/O error, dev sdc, sector 0
[  159.703817] end_request: I/O error, dev sdc, sector 0
[  159.704615] end_request: I/O error, dev sdc, sector 0
[  159.716263] end_request: I/O error, dev sdc, sector 63
[  159.717007] end_request: I/O error, dev sdc, sector 63
[  159.717644] end_request: I/O error, dev sdc, sector 65
[  159.741349] end_request: I/O error, dev sdc, sector 80325
[  159.742141] end_request: I/O error, dev sdc, sector 80325
[  159.742928] end_request: I/O error, dev sdc, sector 80327
[  159.855616] end_request: I/O error, dev sdc, sector 63
[  159.856401] end_request: I/O error, dev sdc, sector 63
[  159.857213] end_request: I/O error, dev sdc, sector 65
[  159.868648] end_request: I/O error, dev sdc, sector 0
[  159.869445] end_request: I/O error, dev sdc, sector 8
[  159.870201] end_request: I/O error, dev sdc, sector 0
[  159.871012] end_request: I/O error, dev sdc, sector 0
[  159.925482] end_request: I/O error, dev sdc, sector 80325
[  159.926284] end_request: I/O error, dev sdc, sector 80325
[  159.927092] end_request: I/O error, dev sdc, sector 80327
[  159.930992] end_request: I/O error, dev sdc, sector 0
[  159.931807] end_request: I/O error, dev sdc, sector 8
[  159.932588] end_request: I/O error, dev sdc, sector 0
[  159.933582] end_request: I/O error, dev sdc, sector 0
[  162.029736] end_request: I/O error, dev sdc, sector 0
[  162.030604] end_request: I/O error, dev sdc, sector 0
[  162.031460] end_request: I/O error, dev sdc, sector 0
```

Any ideas on solving this?

---

