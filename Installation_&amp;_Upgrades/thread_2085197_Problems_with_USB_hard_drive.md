---
title: "Problems with USB hard drive"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by TakeLifeEasy on 2012-11-17
This thread relates to errors with USB drives dropping off from the USB bus.

My Hitachi Touro 2GB connected to either 12.04 or 12.10 just kept dropping out.  I ran "sudo rmmod uas" which I thought cured the problem but it keeps dropping out.  The drive is a USB 3 drive and I have plugged into into USB 2 port on my laptop.

---

### Post by TakeLifeEasy on 2012-11-17
Please see below the errors I am getting

---

### Post by TakeLifeEasy on 2012-11-17
[UPDATE] Just noticed coping large files through rsync made the drive drop out and disappear again :(  Interesting by copying the file through Gnome Shell, I do not get this problem!

This is what the log says -

> Nov 17 15:30:31 coralreef kernel: [13315.520087] usb 1-3: reset high-speed USB device number 11 using ehci_hcd
Nov 17 15:30:46 coralreef kernel: [13330.632136] usb 1-3: device descriptor read/64, error -110
Nov 17 15:31:01 coralreef kernel: [13345.848076] usb 1-3: device descriptor read/64, error -110
Nov 17 15:31:02 coralreef kernel: [13346.064055] usb 1-3: reset high-speed USB device number 11 using ehci_hcd
Nov 17 15:31:17 coralreef kernel: [13361.176101] usb 1-3: device descriptor read/64, error -110
Nov 17 15:31:32 coralreef kernel: [13376.392106] usb 1-3: device descriptor read/64, error -110
Nov 17 15:31:32 coralreef kernel: [13376.608143] usb 1-3: reset high-speed USB device number 11 using ehci_hcd
Nov 17 15:31:38 coralreef kernel: [13382.020060] usb 1-3: device not accepting address 11, error -71
Nov 17 15:31:38 coralreef kernel: [13382.132089] usb 1-3: reset high-speed USB device number 11 using ehci_hcd
Nov 17 15:31:43 coralreef kernel: [13387.544052] usb 1-3: device not accepting address 11, error -71
Nov 17 15:31:43 coralreef kernel: [13387.544121] usb 1-3: USB disconnect, device number 11
Nov 17 15:31:43 coralreef kernel: [13387.544128] sd 5:0:0:0: Device offlined - not ready after error recovery
Nov 17 15:31:43 coralreef kernel: [13387.544147] sd 5:0:0:0: [sdc] Unhandled error code
Nov 17 15:31:43 coralreef kernel: [13387.544154] sd 5:0:0:0: [sdc]  
Nov 17 15:31:43 coralreef kernel: [13387.544158] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Nov 17 15:31:43 coralreef kernel: [13387.544163] sd 5:0:0:0: [sdc] CDB: 
Nov 17 15:31:43 coralreef kernel: [13387.544167] Read(10): 28 00 5a 97 3e 87 00 00 f0 00
Nov 17 15:31:43 coralreef kernel: [13387.544190] end_request: I/O error, dev sdc, sector 1519861383
Nov 17 15:31:43 coralreef kernel: [13387.544198] Buffer I/O error on device sdc1, logical block 189982665
Nov 17 15:31:43 coralreef kernel: [13387.544212] Buffer I/O error on device sdc1, logical block 189982666
Nov 17 15:31:43 coralreef kernel: [13387.544218] Buffer I/O error on device sdc1, logical block 189982667
Nov 17 15:31:43 coralreef kernel: [13387.544224] Buffer I/O error on device sdc1, logical block 189982668
Nov 17 15:31:43 coralreef kernel: [13387.544229] Buffer I/O error on device sdc1, logical block 189982669
Nov 17 15:31:43 coralreef kernel: [13387.544235] Buffer I/O error on device sdc1, logical block 189982670
Nov 17 15:31:43 coralreef kernel: [13387.544240] Buffer I/O error on device sdc1, logical block 189982671
Nov 17 15:31:43 coralreef kernel: [13387.544246] Buffer I/O error on device sdc1, logical block 189982672
Nov 17 15:31:43 coralreef kernel: [13387.544252] Buffer I/O error on device sdc1, logical block 189982673
Nov 17 15:31:43 coralreef kernel: [13387.551943] sd 5:0:0:0: [sdc] Unhandled error code
Nov 17 15:31:43 coralreef kernel: [13387.551951] sd 5:0:0:0: [sdc]  
Nov 17 15:31:43 coralreef kernel: [13387.551955] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Nov 17 15:31:43 coralreef kernel: [13387.551960] sd 5:0:0:0: [sdc] CDB: 
Nov 17 15:31:43 coralreef kernel: [13387.551963] Read(10): 28 00 5a 97 3f 77 00 00 10 00
Nov 17 15:31:43 coralreef kernel: [13387.551985] end_request: I/O error, dev sdc, sector 1519861623
Nov 17 15:31:43 coralreef ntfs-3g[5816]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error

---

### Post by oldos2er on 2012-11-17
Posts moved to their own thread.

---

### Post by TakeLifeEasy on 2012-11-17
[UPDATE 2]  Unfortunately, I spoke too soon and although I can get the drive mounted since running the udo rmmod uas command, as soon as you push a few GB's of data to the drive, it drops off the USB bus :mad:

The drive connect OK -
> Nov 17 18:18:33 coralreef mtp-probe: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3"
Nov 17 18:18:33 coralreef mtp-probe: bus: 1, device: 14 was not an MTP device
Nov 17 18:18:33 coralreef kernel: [  219.006464] Initializing USB Mass Storage driver...
Nov 17 18:18:33 coralreef kernel: [  219.018966] scsi2 : usb-storage 1-3:1.0
Nov 17 18:18:33 coralreef kernel: [  219.019076] usbcore: registered new interface driver usb-storage
Nov 17 18:18:33 coralreef kernel: [  219.019079] USB Mass Storage support registered.
Nov 17 18:18:37 coralreef kernel: [  223.947902] scsi 2:0:0:0: Direct-Access     Hitachi  Hitachi HDS72302 A800 PQ: 0 ANSI: 4
Nov 17 18:18:37 coralreef kernel: [  223.949794] sd 2:0:0:0: Attached scsi generic sg2 type 0
Nov 17 18:18:37 coralreef kernel: [  223.950125] sd 2:0:0:0: [sdb] 3907024896 512-byte logical blocks: (2.00 TB/1.81 TiB)
Nov 17 18:18:37 coralreef kernel: [  223.953014] sd 2:0:0:0: [sdb] Write Protect is off
Nov 17 18:18:37 coralreef kernel: [  223.953023] sd 2:0:0:0: [sdb] Mode Sense: 4b 00 10 08
Nov 17 18:18:37 coralreef kernel: [  223.953888] sd 2:0:0:0: [sdb] No Caching mode page present
Nov 17 18:18:37 coralreef kernel: [  223.953895] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Nov 17 18:18:37 coralreef kernel: [  223.956771] sd 2:0:0:0: [sdb] No Caching mode page present
Nov 17 18:18:37 coralreef kernel: [  223.956779] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Nov 17 18:18:37 coralreef kernel: [  223.977976]  sdb: sdb1
Nov 17 18:18:37 coralreef ata_id[3362]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Nov 17 18:18:37 coralreef kernel: [  223.980753] sd 2:0:0:0: [sdb] No Caching mode page present
Nov 17 18:18:37 coralreef kernel: [  223.980758] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Nov 17 18:18:37 coralreef kernel: [  223.980762] sd 2:0:0:0: [sdb] Attached SCSI disk
Nov 17 18:18:38 coralreef kernel: [  224.505799] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)

Interesting when I refresh Gparted to look for the attached drive, the sys log lists -

> Nov 17 18:23:47 coralreef ata_id[3598]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Nov 17 18:23:47 coralreef ata_id[3610]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Nov 17 18:23:50 coralreef ata_id[3648]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Nov 17 18:23:51 coralreef ata_id[3657]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument

I get the same message when I un mount it.

I have re-partitioned the drive from NTFS to ext4, and it makes no difference, when pushing the drive, error begins all over again and then the drive disappears off the bus :mad:

> Nov 17 18:26:08 coralreef kernel: [  674.096050] usb 1-3: reset high-speed USB device number 14 using ehci_hcd
Nov 17 18:26:23 coralreef kernel: [  689.208084] usb 1-3: device descriptor read/64, error -110
Nov 17 18:26:38 coralreef kernel: [  704.424067] usb 1-3: device descriptor read/64, error -110
Nov 17 18:26:38 coralreef kernel: [  704.640085] usb 1-3: reset high-speed USB device number 14 using ehci_hcd
Nov 17 18:26:53 coralreef kernel: [  719.752077] usb 1-3: device descriptor read/64, error -110
Nov 17 18:27:08 coralreef kernel: [  734.968079] usb 1-3: device descriptor read/64, error -110
Nov 17 18:27:09 coralreef kernel: [  735.184060] usb 1-3: reset high-speed USB device number 14 using ehci_hcd
Nov 17 18:27:14 coralreef kernel: [  740.596055] usb 1-3: device not accepting address 14, error -71
Nov 17 18:27:14 coralreef kernel: [  740.708058] usb 1-3: reset high-speed USB device number 14 using ehci_hcd
Nov 17 18:27:20 coralreef kernel: [  746.120070] usb 1-3: device not accepting address 14, error -71
Nov 17 18:27:20 coralreef kernel: [  746.120128] usb 1-3: USB disconnect, device number 14
Nov 17 18:27:20 coralreef kernel: [  746.120131] sd 2:0:0:0: Device offlined - not ready after error recovery
Nov 17 18:27:20 coralreef kernel: [  746.120139] sd 2:0:0:0: [sdb] Unhandled error code
Nov 17 18:27:20 coralreef kernel: [  746.120142] sd 2:0:0:0: [sdb]  
Nov 17 18:27:20 coralreef kernel: [  746.120144] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Nov 17 18:27:20 coralreef kernel: [  746.120146] sd 2:0:0:0: [sdb] CDB: 
Nov 17 18:27:20 coralreef kernel: [  746.120148] Read(10): 28 00 ce 00 08 00 00 00 08 00
Nov 17 18:27:20 coralreef kernel: [  746.120159] end_request: I/O error, dev sdb, sector 3456108544
Nov 17 18:27:20 coralreef kernel: [  746.120163] Buffer I/O error on device sdb1, logical block 432013312
Nov 17 18:27:20 coralreef kernel: [  746.120191] sd 2:0:0:0: rejecting I/O to offline device
Nov 17 18:27:20 coralreef kernel: [  746.131487] Buffer I/O error on device sdb1, logical block 433061888
Nov 17 18:27:20 coralreef kernel: [  746.131495] Buffer I/O error on device sdb1, logical block 433061888
Nov 17 18:27:20 coralreef kernel: [  746.137920] Buffer I/O error on device sdb1, logical block 433586176
Nov 17 18:27:20 coralreef kernel: [  746.151432] Buffer I/O error on device sdb1, logical block 434110464
Nov 17 18:27:20 coralreef kernel: [  746.154423] Buffer I/O error on device sdb1, logical block 434634752
Nov 17 18:27:20 coralreef kernel: [  746.157313] Buffer I/O error on device sdb1, logical block 435159040
Nov 17 18:27:20 coralreef kernel: [  746.160210] Buffer I/O error on device sdb1, logical block 435683328
Nov 17 18:27:20 coralreef kernel: [  746.163037] Buffer I/O error on device sdb1, logical block 436207616
Nov 17 18:27:20 coralreef kernel: [  746.166493] Buffer I/O error on device sdb1, logical block 436731904
Nov 17 18:27:20 coralreef kernel: [  746.240047] usb 1-3: new high-speed USB device number 15 using ehci_hcd
Nov 17 18:27:27 coralreef kernel: [  753.479655] quiet_error: 99 callbacks suppressed
Nov 17 18:27:27 coralreef kernel: [  753.479660] Buffer I/O error on device sdb1, logical block 32768
Nov 17 18:27:27 coralreef kernel: [  753.479711] Buffer I/O error on device sdb1, logical block 98304
Nov 17 18:27:27 coralreef kernel: [  753.479741] Buffer I/O error on device sdb1, logical block 163840
Nov 17 18:27:27 coralreef kernel: [  753.479770] Buffer I/O error on device sdb1, logical block 229376
Nov 17 18:27:27 coralreef kernel: [  753.479799] Buffer I/O error on device sdb1, logical block 294912
Nov 17 18:27:27 coralreef kernel: [  753.479832] Buffer I/O error on device sdb1, logical block 819200
Nov 17 18:27:27 coralreef kernel: [  753.479863] Buffer I/O error on device sdb1, logical block 884736
Nov 17 18:27:27 coralreef kernel: [  753.479895] Buffer I/O error on device sdb1, logical block 1605632
Nov 17 18:27:27 coralreef kernel: [  753.479927] Buffer I/O error on device sdb1, logical block 2654208
Nov 17 18:27:27 coralreef kernel: [  753.479960] Buffer I/O error on device sdb1, logical block 4096000
Nov 17 18:27:35 coralreef kernel: [  761.352064] usb 1-3: device descriptor read/64, error -110
Nov 17 18:27:50 coralreef kernel: [  776.568121] usb 1-3: device descriptor read/64, error -110
Nov 17 18:27:50 coralreef kernel: [  776.784073] usb 1-3: new high-speed USB device number 16 using ehci_hcd
Nov 17 18:28:05 coralreef kernel: [  791.896123] usb 1-3: device descriptor read/64, error -110
Nov 17 18:28:21 coralreef kernel: [  807.112073] usb 1-3: device descriptor read/64, error -110
Nov 17 18:28:21 coralreef kernel: [  807.328136] usb 1-3: new high-speed USB device number 17 using ehci_hcd
Nov 17 18:28:26 coralreef kernel: [  812.740035] usb 1-3: device not accepting address 17, error -71
Nov 17 18:28:26 coralreef kernel: [  812.852058] usb 1-3: new high-speed USB device number 18 using ehci_hcd
Nov 17 18:28:32 coralreef kernel: [  818.264076] usb 1-3: device not accepting address 18, error -71
Nov 17 18:28:32 coralreef kernel: [  818.264109] hub 1-0:1.0: unable to enumerate USB device on port 3
Nov 17 18:28:32 coralreef kernel: [  818.656130] usb 3-1: new full-speed USB device number 3 using uhci_hcd
Nov 17 18:28:47 coralreef kernel: [  833.768122] usb 3-1: device descriptor read/64, error -110
Nov 17 18:29:03 coralreef kernel: [  848.984110] usb 3-1: device descriptor read/64, error -110
Nov 17 18:29:03 coralreef kernel: [  849.200071] usb 3-1: new full-speed USB device number 4 using uhci_hcd
Nov 17 18:29:18 coralreef kernel: [  864.312111] usb 3-1: device descriptor read/64, error -110
Nov 17 18:29:33 coralreef kernel: [  879.528132] usb 3-1: device descriptor read/64, error -110
Nov 17 18:29:33 coralreef kernel: [  879.744101] usb 3-1: new full-speed USB device number 5 using uhci_hcd
Nov 17 18:29:39 coralreef kernel: [  885.156114] usb 3-1: device not accepting address 5, error -84
Nov 17 18:29:39 coralreef kernel: [  885.268132] usb 3-1: new full-speed USB device number 6 using uhci_hcd
Nov 17 18:29:44 coralreef kernel: [  890.680117] usb 3-1: device not accepting address 6, error -84
Nov 17 18:29:44 coralreef kernel: [  890.680152] hub 3-0:1.0: unable to enumerate USB device on port 1

---

### Post by TakeLifeEasy on 2012-11-18
I have been some further research on this and come accross the follow issue which Linus Torvalds found! Could this be related to this issue?
[https://lkml.org/lkml/2012/4/14/217](https://lkml.org/lkml/2012/4/14/217)

---

