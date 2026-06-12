---
title: "Nerolinux verification failure with Taiyo Yuden"
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by RaZoR1394 on 2009-02-25
Hello.

My Taiyo Yuden's are not verifying correctly and there are errors in dmesg.

```

[   57.838016] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   57.838021] sr 3:0:0:0: [sr0] Sense Key : Blank Check [current] 
[   57.838025] sr 3:0:0:0: [sr0] Add. Sense: No additional sense information
[   57.838028] end_request: I/O error, dev sr0, sector 0
[   57.838033] Buffer I/O error on device sr0, logical block 0
[   57.850009] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   57.850011] sr 3:0:0:0: [sr0] Sense Key : Blank Check [current] 
[   57.850014] sr 3:0:0:0: [sr0] Add. Sense: No additional sense information
[   57.850017] end_request: I/O error, dev sr0, sector 0
[   57.850019] Buffer I/O error on device sr0, logical block 0

```

I've made five coasters already and I don't feel like I want more of those. Nerolinux has almost always worked great, specially with these discs. I noticed this right before yesterday but it was only one disc and it seemed to have a physical defect. I'm burning my Taiyo Yuden:s in 20x as always but 4x doesn't help either. I managed to burn one Taiyo Yuden in 4x and also one Verbatim DVD+RW disc in 4x with good verification but that is all.

These problems started about when I got my new WD MyBook 1TB.

Here is another snippet from my dmesg.

```

[   21.091838] ieee1394: sbp2: Logged into SBP-2 device
[   21.094539] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   21.119585] scsi 12:0:0:0: Direct-Access     WD       My Book          1034 PQ: 0 ANSI: 4
[   21.129726] sd 12:0:0:0: [sdh] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[   21.136161] sd 12:0:0:0: [sdh] Write Protect is off
[   21.136163] sd 12:0:0:0: [sdh] Mode Sense: 10 00 00 00
[   21.141417] sd 12:0:0:0: [sdh] Cache data unavailable
[   21.141419] sd 12:0:0:0: [sdh] Assuming drive cache: write through
[   21.151445] sd 12:0:0:0: [sdh] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[   21.158004] sd 12:0:0:0: [sdh] Write Protect is off
[   21.158006] sd 12:0:0:0: [sdh] Mode Sense: 10 00 00 00
[   21.163343] sd 12:0:0:0: [sdh] Cache data unavailable
[   21.163344] sd 12:0:0:0: [sdh] Assuming drive cache: write through
[   21.163348]  sdh: sdh1
[   21.646447] sd 12:0:0:0: [sdh] Attached SCSI disk
[   21.646505] sd 12:0:0:0: Attached scsi generic sg8 type 0
[   21.647965] scsi13 : SBP-2 IEEE-1394
[   23.261939] ieee1394: sbp2: Logged into SBP-2 device
[   23.264740] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   23.289489] scsi 13:0:1:0: Enclosure         WD       My Book Device        PQ: 0 ANSI: 4
[   23.289603] scsi 13:0:1:0: Attached scsi generic sg9 type 13
[   23.289726] ------------[ cut here ]------------
[   23.289728] WARNING: at /build/buildd/linux-2.6.28/fs/sysfs/dir.c:462 sysfs_add_one+0x49/0x50()
[   23.289730] sysfs: duplicate filename '0090a97999e4b0db-1' can not be created
[   23.289732] Modules linked in: sbp2 sata_mv skge ohci1394 ieee1394 forcedeth ehci_hcd ohci_hcd fbcon tileblit font bitblit softcursor fuse
[   23.289745] Pid: 1158, comm: knodemgrd_0 Not tainted 2.6.28-8-generic #26-Ubuntu
[   23.289748] Call Trace:
[   23.289757]  [<c0139a70>] warn_slowpath+0x60/0x80
[   23.289763]  [<c012ad96>] ? dequeue_entity+0x16/0x2a0
[   23.289769]  [<c02bd0f2>] ? idr_get_empty_slot+0xe2/0x270
[   23.289772]  [<c02bd304>] ? ida_get_new_above+0x84/0x1c0
[   23.289775]  [<c020ae00>] ? sysfs_ilookup_test+0x0/0x20
[   23.289778]  [<c020ae00>] ? sysfs_ilookup_test+0x0/0x20
[   23.289780]  [<c020b111>] ? sysfs_find_dirent+0x21/0x30
[   23.289783]  [<c020b1c3>] ? __sysfs_add_one+0x13/0x90
[   23.289786]  [<c020b399>] sysfs_add_one+0x49/0x50
[   23.289788]  [<c020c191>] sysfs_do_create_link+0xd1/0x120
[   23.289791]  [<c020c212>] sysfs_create_link+0x12/0x20
[   23.289795]  [<c0345bd9>] driver_sysfs_add+0x29/0x70
[   23.289798]  [<c0345f14>] device_bind_driver+0x14/0x30
[   23.289801]  [<c0345f64>] device_attach+0x34/0x80
[   23.289803]  [<c0344cc0>] bus_rescan_devices_helper+0x40/0x70
[   23.289806]  [<c0345623>] bus_for_each_dev+0x53/0x80
[   23.289809]  [<c0345666>] bus_rescan_devices+0x16/0x20
[   23.289812]  [<c0344c80>] ? bus_rescan_devices_helper+0x0/0x70
[   23.289824]  [<f7d14ccd>] nodemgr_host_thread+0x29d/0x350 [ieee1394]
[   23.289832]  [<f7d15600>] ? node_probe+0x0/0x60 [ieee1394]
[   23.289840]  [<f7d14a30>] ? nodemgr_host_thread+0x0/0x350 [ieee1394]
[   23.289843]  [<c014e89c>] kthread+0x3c/0x70
[   23.289846]  [<c014e860>] ? kthread+0x0/0x70
[   23.289849]  [<c0105477>] kernel_thread_helper+0x7/0x10
[   23.289851] ---[ end trace 9f0271da25b90e02 ]---

```

See attachment for full dmesg.

I'm currently passing all_generic_ide but it doesn't help.

I'm wondering if the drive is defective. Shouldn't be any surprise with WD MyBook don't you think?

---

### Post by RaZoR1394 on 2009-02-25
I burnt files straight of my main system drive and I got the same results. :mad:

---

### Post by RaZoR1394 on 2009-02-26
Ok, so It's a linux issue it seems. I'm running the previous vmlinuz-2.6.28-7-generic and It's working fine.

---

