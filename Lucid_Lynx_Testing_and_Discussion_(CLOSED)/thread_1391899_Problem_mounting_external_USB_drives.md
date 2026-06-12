---
title: "Problem mounting external USB drives"
date: 2010-01-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by moviemaniac on 2010-01-27
Hi guys,

has anyone of you experienced this problem too? I have several ext3 hard drives which worked fine in Karmic and other machines. 
However when I plug them in on lucid they only get mounted on the first time after every reboot, it is not possible to remove and remount them during one session. When I connect them and fire up the Disk Utility it tells me there's only free space on the hdd and I get the following entries in my syslog:

```
Jan 27 17:27:47 klaus-imac kernel: [  116.220416] usb-storage: device scan complete
Jan 27 17:27:47 klaus-imac kernel: [  116.222506] scsi 6:0:0:0: Direct-Access     TOSHIBA  MK5055GSX        0002 PQ: 0 ANSI: 0
Jan 27 17:27:47 klaus-imac kernel: [  116.222823] sd 6:0:0:0: Attached scsi generic sg3 type 0
Jan 27 17:27:47 klaus-imac kernel: [  116.225149] sd 6:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jan 27 17:27:47 klaus-imac kernel: [  116.225998] sd 6:0:0:0: [sdb] Write Protect is off
Jan 27 17:27:47 klaus-imac kernel: [  116.226000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
Jan 27 17:27:47 klaus-imac kernel: [  116.226002] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Jan 27 17:27:47 klaus-imac kernel: [  116.227509] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Jan 27 17:27:47 klaus-imac kernel: [  116.227511]  sdb: sdb1
Jan 27 17:27:47 klaus-imac kernel: [  116.263544] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Jan 27 17:27:47 klaus-imac kernel: [  116.263549] sd 6:0:0:0: [sdb] Attached SCSI disk
Jan 27 17:27:55 klaus-imac kernel: [  124.120514] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:28:03 klaus-imac kernel: [  132.120379] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
```

any ideas? It would even help me to know which package to file a bug against...


//edit: LUKS-encrypted drives (also formatted with ext3), FAT32 USB thumb drives and HFS+ drives work just fine, it's just plain ext3 drives making trouble...


//edit2: more errors from kern.log:

```
Jan 27 17:30:07 klaus-imac kernel: [  256.130303] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:30:11 klaus-imac kernel: [  260.419828] applesmc: wait status failed: 5 != 0
Jan 27 17:30:38 klaus-imac kernel: [  287.121304] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:31:03 klaus-imac kernel: [  312.501640] kjournald starting.  Commit interval 5 seconds
Jan 27 17:31:03 klaus-imac kernel: [  312.501644] EXT3-fs warning: checktime reached, running e2fsck is recommended
Jan 27 17:31:03 klaus-imac kernel: [  312.510681] EXT3 FS on dm-0, internal journal
Jan 27 17:31:03 klaus-imac kernel: [  312.510685] EXT3-fs: mounted filesystem with writeback data mode.
Jan 27 17:31:09 klaus-imac kernel: [  318.090472] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:31:09 klaus-imac kernel: [  318.202065] sd 6:0:0:0: [sdb] Unhandled error code
Jan 27 17:31:09 klaus-imac kernel: [  318.202074] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Jan 27 17:31:09 klaus-imac kernel: [  318.202083] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 20 00
Jan 27 17:31:09 klaus-imac kernel: [  318.202104] end_request: I/O error, dev sdb, sector 0
Jan 27 17:31:09 klaus-imac kernel: [  318.202115] Buffer I/O error on device sdb, logical block 0
Jan 27 17:31:09 klaus-imac kernel: [  318.202126] Buffer I/O error on device sdb, logical block 1
Jan 27 17:31:09 klaus-imac kernel: [  318.202133] Buffer I/O error on device sdb, logical block 2
Jan 27 17:31:09 klaus-imac kernel: [  318.202140] Buffer I/O error on device sdb, logical block 3
Jan 27 17:31:40 klaus-imac kernel: [  349.092930] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:32:11 klaus-imac kernel: [  380.090465] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:32:42 klaus-imac kernel: [  411.096963] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:33:13 klaus-imac kernel: [  442.090455] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:33:44 klaus-imac kernel: [  473.130475] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:34:15 klaus-imac kernel: [  504.122969] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:34:15 klaus-imac kernel: [  504.234568] sd 6:0:0:0: [sdb] Unhandled error code
Jan 27 17:34:15 klaus-imac kernel: [  504.234577] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Jan 27 17:34:15 klaus-imac kernel: [  504.234586] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 f0 00
Jan 27 17:34:15 klaus-imac kernel: [  504.234608] end_request: I/O error, dev sdb, sector 63
Jan 27 17:34:15 klaus-imac kernel: [  504.234620] Buffer I/O error on device sdb1, logical block 0
Jan 27 17:34:15 klaus-imac kernel: [  504.234630] Buffer I/O error on device sdb1, logical block 1
Jan 27 17:34:15 klaus-imac kernel: [  504.234638] Buffer I/O error on device sdb1, logical block 2
Jan 27 17:34:15 klaus-imac kernel: [  504.234644] Buffer I/O error on device sdb1, logical block 3
Jan 27 17:34:15 klaus-imac kernel: [  504.234658] Buffer I/O error on device sdb1, logical block 4
Jan 27 17:34:15 klaus-imac kernel: [  504.234664] Buffer I/O error on device sdb1, logical block 5
Jan 27 17:34:15 klaus-imac kernel: [  504.234671] Buffer I/O error on device sdb1, logical block 6
Jan 27 17:34:15 klaus-imac kernel: [  504.234677] Buffer I/O error on device sdb1, logical block 7
Jan 27 17:34:15 klaus-imac kernel: [  504.234684] Buffer I/O error on device sdb1, logical block 8
Jan 27 17:34:15 klaus-imac kernel: [  504.234690] Buffer I/O error on device sdb1, logical block 9
Jan 27 17:34:46 klaus-imac kernel: [  535.090446] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:35:17 klaus-imac kernel: [  566.120432] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:35:48 klaus-imac kernel: [  597.122905] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:36:19 klaus-imac kernel: [  628.120448] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:36:50 klaus-imac kernel: [  659.090435] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:37:21 klaus-imac kernel: [  690.100430] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:37:21 klaus-imac kernel: [  690.204190] sd 6:0:0:0: [sdb] Unhandled error code
Jan 27 17:37:21 klaus-imac kernel: [  690.204200] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Jan 27 17:37:21 klaus-imac kernel: [  690.204204] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 2f 00 00 10 00
Jan 27 17:37:21 klaus-imac kernel: [  690.204213] end_request: I/O error, dev sdb, sector 303
Jan 27 17:37:21 klaus-imac kernel: [  690.204218] __ratelimit: 110 callbacks suppressed
Jan 27 17:37:21 klaus-imac kernel: [  690.204221] Buffer I/O error on device sdb1, logical block 120
Jan 27 17:37:21 klaus-imac kernel: [  690.204225] Buffer I/O error on device sdb1, logical block 121
Jan 27 17:37:21 klaus-imac kernel: [  690.204228] Buffer I/O error on device sdb1, logical block 122
Jan 27 17:37:21 klaus-imac kernel: [  690.204230] Buffer I/O error on device sdb1, logical block 123
Jan 27 17:37:21 klaus-imac kernel: [  690.204234] Buffer I/O error on device sdb1, logical block 124
Jan 27 17:37:21 klaus-imac kernel: [  690.204236] Buffer I/O error on device sdb1, logical block 125
Jan 27 17:37:21 klaus-imac kernel: [  690.204239] Buffer I/O error on device sdb1, logical block 126
Jan 27 17:37:21 klaus-imac kernel: [  690.204242] Buffer I/O error on device sdb1, logical block 127
Jan 27 17:37:52 klaus-imac kernel: [  721.122941] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:38:23 klaus-imac kernel: [  752.092932] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:38:54 klaus-imac kernel: [  783.092942] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:39:25 klaus-imac kernel: [  814.093405] usb 2-1.4: reset high speed USB device using ehci_hcd and address 6
Jan 27 17:39:28 klaus-imac kernel: [  817.584599] sd 6:0:0:0: timing out command, waited 180s
Jan 27 17:39:28 klaus-imac kernel: [  817.584621] sd 6:0:0:0: [sdb] Unhandled error code
Jan 27 17:39:28 klaus-imac kernel: [  817.584626] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Jan 27 17:39:28 klaus-imac kernel: [  817.584636] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
Jan 27 17:39:28 klaus-imac kernel: [  817.584657] end_request: I/O error, dev sdb, sector 63
Jan 27 17:39:28 klaus-imac kernel: [  817.584667] Buffer I/O error on device sdb1, logical block 0
Jan 27 17:39:28 klaus-imac kernel: [  817.584678] Buffer I/O error on device sdb1, logical block 1
Jan 27 17:39:28 klaus-imac kernel: [  817.584685] Buffer I/O error on device sdb1, logical block 2
Jan 27 17:39:28 klaus-imac kernel: [  817.584691] Buffer I/O error on device sdb1, logical block 3
```

---

### Post by VMC on 2010-01-27
I just tried it, and it works ok. You use unmount or safely remove drive?

---

### Post by moviemaniac on 2010-01-28
Yes, the drives are always safely removed.

---

### Post by moviemaniac on 2010-01-28
I could just reproduce the bug on my brother's Lenovo T500 with the same hard drive. What's really strange is, is that I have several external hard drives from the same company using the same chipsets but some show the mentioned bug and some don't...

---

### Post by moviemaniac on 2010-01-29
Okay, after trying several things and examining the hardware closely I think it's a bug in either a driver or the hardware. The issue concerns hard drive enclosures identifying themselves as "05e3:0718 Genesys Logic, Inc." and I think I've seen a connection with intel ICH8-chipsets, too, studying several bugreports regarding these enclosures.

External hard drives using this chipset fail on all 2.6.32-kernels I've tried (up to 2.6.32-7 vanilla) - regardless of the file system as I erroneously thought in the first place. I haven't found a fix or a solution for it - other than using a different USB enclosure...

//edit: Tested yet another USB drive and it's also happening with one from a different Chip vendor (Jmicron) so that leaves me back at the beginning, completely clueless.

---

### Post by heldal on 2010-01-30
It looks like a problem with kernel 2.6.32 to me. A 500GB WD drive that worked fine with 2.6.31 (9.04) failed with 2.6.32. I assumed the drive was broken and got a replacement. The new device is a Samsung drive in a Verbatim enclosure with external power-supply, but this also fails on heavy I/O. I've also tried a 3rd combination of enclosure and HD and got the same problem, as well as tested with a different motherboard/chipset. The problem is most likely in USB or chipset drivers as it affects all types of filesystems (tested FAT32/ext3/ext4/truecrypt).

I'm using homebrew kernels, and I'm now building 2.6.31.12 to see if that is working any better. 

The problem with resetting/disconneting USB-drives has also been reported on kernel.org in relation to 2.6.33-rc so it may be an issue that has been introduced with 2.6.32 and not yet been resolved.

---

### Post by moviemaniac on 2010-01-30
Thanks for your post, heldal! The very strange thing is that some drives work perfectly _every time_ I use them and others refuse to work _at all_. I've got two identical external enclosures - bought 1 year apart. I looked at the boards and they're absolutely identical - except for the revision of the controller chip. The older one works, the newer one fails. 

I've written about the bug on the linux-usb list as I think this is the one where the issue should be discussed and reaches most people. 

Sadly I can't get back to .31 because of some newer drivers on my system that need a .32 kernel but let me know how it works for you!

---

### Post by heldal on 2010-01-30
My WD-passport drive (1058:0704) that I suspected was broken works fine with kernel 2.6.31.12. 

2.6.31.X alone doesn't solve all problems though. I had to decrease max_sectors from 240 to 120 to avoid periodic resets with  a Verbatim drive (18a5:0218).
[INDENT]
sudo sh -c "echo 120 > /sys/block/sdX/device/max_sectors"
   ... where X is a/b/c... depending on drive order.
[/INDENT]

I also found a few useful tips  [here]("https://help.ubuntu.com/community/Mount/USB")

More testing is needed. But I've written and verified about 50GB on each drive so far without any errors.

---

### Post by kha on 2010-01-30
Hi,

I've searched all the day for my issue and it seems related to this topic also... Could you please confirm and explain me how it could be resolved ?

I've bought a Western Digital Portable Driver (Passeport Essential SE, 1TB). I took this one because I saw that other WD portable drives were working on Linux, and i needed a 1TB drive. I saw that it supports encryption but i didn't think it could cause any issue since I was hoping it could be entirely low level reformatted easily... Like U3 USB sticks..

When i connect it on my Ubuntu 9.10 kernel 2.6.31-16-generic, the only drive showing is the 500Mo UDF (CD) drive at /dev/sr1 which is of course read-only. 

I would like to reset and format the disk entirely to EXT4 filesystem... How can i do ? I cannot access anything on the disk even if i set my encryption password on my Windows Virtual Machine.

root@box:~# fdisk /dev/sdb
Unable to read /dev/sdb

root@box:~# scsiinfo -l
/dev/sda /dev/sdb /dev/scd0 /dev/scd1

root@box:~# lsusb
Bus 001 Device 009: ID 1058:070a Western Digital Technologies, Inc.

root@box:~# dmesg
Jan 30 23:40:31 box kernel: [43964.424065] usb 1-3: new high speed USB device using ehci_hcd and address 9
Jan 30 23:40:31 box kernel: [43964.561643] usb 1-3: configuration #1 chosen from 1 choice
Jan 30 23:40:31 box kernel: [43964.562693] scsi13 : SCSI emulation for USB Mass Storage devices
Jan 30 23:40:36 box kernel: [43969.561251] scsi 13:0:0:0: Direct-Access     WD       My Passport 070A 1030 PQ: 0 ANSI: 4
Jan 30 23:40:36 box kernel: [43969.562111] scsi 13:0:0:1: CD-ROM            WD       Virtual CD 070A  1030 PQ: 0 ANSI: 4
Jan 30 23:40:36 box kernel: [43969.562985] scsi 13:0:0:2: Enclosure         WD       SES Device       1030 PQ: 0 ANSI: 4
Jan 30 23:40:36 box kernel: [43969.563765] sd 13:0:0:0: Attached scsi generic sg2 type 0
Jan 30 23:40:36 box kernel: [43969.574412] sr1: scsi3-mmc drive: 51x/51x caddy
Jan 30 23:40:36 box kernel: [43969.574757] sr 13:0:0:1: Attached scsi generic sg3 type 5
Jan 30 23:40:36 box kernel: [43969.574859] ses 13:0:0:2: Attached Enclosure device
Jan 30 23:40:36 box kernel: [43969.574949] ses 13:0:0:2: Attached scsi generic sg4 type 13
Jan 30 23:40:36 box kernel: [43969.603270] sd 13:0:0:0: [sdb] Unit Not Ready
Jan 30 23:40:36 box kernel: [43969.603275] sd 13:0:0:0: [sdb] Sense Key : Data Protect [current] 
Jan 30 23:40:36 box kernel: [43969.603281] sd 13:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
Jan 30 23:40:36 box kernel: [43969.606586] sd 13:0:0:0: [sdb] 1952151552 512-byte logical blocks: (999 GB/930 GiB)
Jan 30 23:40:36 box kernel: [43969.608386] sd 13:0:0:0: [sdb] Write Protect is off
Jan 30 23:40:36 box kernel: [43969.612077] sd 13:0:0:0: [sdb] Unit Not Ready
Jan 30 23:40:36 box kernel: [43969.612083] sd 13:0:0:0: [sdb] Sense Key : Data Protect [current] 
Jan 30 23:40:36 box kernel: [43969.612088] sd 13:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
Jan 30 23:40:36 box kernel: [43969.616331]  sdb:
Jan 30 23:40:36 box kernel: [43969.617691] sd 13:0:0:0: [sdb] Unhandled sense code
Jan 30 23:40:36 box kernel: [43969.617694] sd 13:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 30 23:40:36 box kernel: [43969.617698] sd 13:0:0:0: [sdb] Sense Key : Data Protect [current] 
Jan 30 23:40:36 box kernel: [43969.617703] sd 13:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
Jan 30 23:40:36 box kernel: [43969.617715] __ratelimit: 77 callbacks suppressed
Jan 30 23:40:36 box kernel: [43969.619436] sd 13:0:0:0: [sdb] Unhandled sense code
Jan 30 23:40:36 box kernel: [43969.619439] sd 13:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 30 23:40:36 box kernel: [43969.619442] sd 13:0:0:0: [sdb] Sense Key : Data Protect [current] 
Jan 30 23:40:36 box kernel: [43969.619447] sd 13:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[...]
Jan 30 23:40:36 box kernel: [43969.671143] Dev sdb: unable to read RDB block 0
Jan 30 23:40:36 box kernel: [43969.672063] sd 13:0:0:0: [sdb] Unhandled sense code
Jan 30 23:40:36 box kernel: [43969.672066] sd 13:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 30 23:40:36 box kernel: [43969.672069] sd 13:0:0:0: [sdb] Sense Key : Data Protect [current] 
Jan 30 23:40:36 box kernel: [43969.672074] sd 13:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[...]
Jan 30 23:40:36 box kernel: [43969.682721]  unable to read partition table
Jan 30 23:40:36 box kernel: [43969.687950] sd 13:0:0:0: [sdb] Unit Not Ready
Jan 30 23:40:36 box kernel: [43969.687954] sd 13:0:0:0: [sdb] Sense Key : Data Protect [current] 
Jan 30 23:40:36 box kernel: [43969.687959] sd 13:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
Jan 30 23:40:36 box kernel: [43969.691870] sd 13:0:0:0: [sdb] Attached SCSI disk
Jan 30 23:40:36 box kernel: [43969.693814] sd 13:0:0:0: [sdb] Unhandled sense code
Jan 30 23:40:36 box kernel: [43969.693817] sd 13:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 30 23:40:36 box kernel: [43969.693821] sd 13:0:0:0: [sdb] Sense Key : Data Protect [current] 
Jan 30 23:40:36 box kernel: [43969.693826] sd 13:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[...]
Jan 30 23:40:36 box kernel: [43969.985819] UDF-fs: Partition marked readonly; forcing readonly mount
Jan 30 23:40:36 box kernel: [43969.986315] UDF-fs INFO UDF: Mounting volume 'WD SmartWare', timestamp 2009/09/11 14:33 (1ed4)
Jan 30 23:40:37 box kernel: [43970.284931] sd 13:0:0:0: [sdb] Unhandled sense code
Jan 30 23:40:37 box kernel: [43970.284937] sd 13:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 30 23:40:37 box kernel: [43970.284941] sd 13:0:0:0: [sdb] Sense Key : Data Protect [current] 
Jan 30 23:40:37 box kernel: [43970.284947] sd 13:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[...]

---

### Post by ranch hand on 2010-01-31
Just out of curiosity you might try turning your internal drive(s) off in bios, and with the external plugged in before you start, boot to the live cd.

This should see the external as the only drive and may allow you access that way.

Just a guess that I would try.  Amazing some of the things those LiveCDs are good for.

---

### Post by moviemaniac on 2010-01-31
Thanks for the suggestion but I don't think it's gonna get us far. The culprit - as Alan Stern found out on linux-usb - are two ATA pass-through-commands:

> The usbmon trace shows the problem clearly, although it doesn't show
the source of the problem.  Things start to go wrong here:

> ffff88001b083e40 2655717029 S Bo:2:015:2 -115 31 = 55534243 21000000 00000000 00001085 06200005 00fe0000 00000000 40ef00
> ffff88001b083e40 2655717090 C Bo:2:015:2 0 31 >
> ffff88001b083e40 2655717123 S Bi:2:015:1 -115 13 <
> ffff88001b083e40 2655731738 C Bi:2:015:1 0 13 = 55534253 21000000 00000000 00
> ffff88001b083e40 2655732007 S Bo:2:015:2 -115 31 = 55534243 22000000 00020000 80001085 082e0000 00000000 00000000 40ec00
> ffff88001b083e40 2655732099 C Bo:2:015:2 0 31 >
> ffff8800afe263c0 2655732126 S Bi:2:015:1 -115 512 <
> ffff8800afe263c0 2655748859 C Bi:2:015:1 -121 13 = 55534253 22000000 00020000 00
> ffff88001b083e40 2655748906 S Bi:2:015:1 -115 13 <
> ffff88001b083e40 2663266469 C Bi:2:015:1 -104 0

The shows a sequence of two ATA pass-through commands being sent to the 
device.  I don't know what those commands are or what program was 
responsible for sending them; as far as I'm aware nothing in the kernel 
will do it.  Perhaps some program started by udev is responsible.  
Looking through your udev rules might pinpoint the culprit.

Anyway, the first command doesn't seem to cause any difficulty, but the 
second command fails completely.  Instead of sending data in its 
response, the device sends a status message.  The kernel gets this, 
thinks it is data, and then waits for the status to come -- which of 
course never happens.  So the kernel resets the device and tries 
issuing the same command again, with the same result.

Alan Stern


Filed a bug against udev:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/515023](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/515023)

---

### Post by heldal on 2010-01-31
To reformat the disk with another filesystem you first have to delete the existing partitions and create new partition(s) for the new filesystem(s). This can be done with commandline tools such as fdisk, parted, mkfs. If you need a GUI there's gparted that can help with the job. It is either started as "Partition Editor" from the "administration" menu, or with the command "sudo gparted". In gparted, choose the appropriate device (/dev/sdb according to your log), select and delete the existing partition(s), then select the free block representing the entire disk and create a new partition across the whole disk (or part of it) and choose the filesystem you want. The filesystem will be mounted automatically as /media/<LABEL> when the drive is re-connected if you give it a label in gparted. When you apply the changes gparted will execute the necessary commands to delete, create and format any changed partitions. 

Note that none of the filesystems on a drive should be mounted when it is repartitioned. To re-partition a system-drive you should thus boot from a live-cd and perform the job from from there.

If you get problems while writing to the new filesystem with lines indicating "reset high speed USB device using ehci_hcd and address X" in /var/log/messages you may need to throttle the device by reducing the transfer buffer as described previously in the thread.

---

### Post by moviemaniac on 2010-01-31
> **heldal said:**
> To reformat the disk with another filesystem you first have to delete the existing partitions[...]
Thanks, but the drive has been formatted correctly (on another machine because this bug prevents me from doing so on any computer running lucid...)

> Note that none of the filesystems on a drive should be mounted when it is repartitioned. To re-partition a system-drive you should thus boot from a live-cd and perform the job from from there.

It's an external drive (making it a non-system one) with one single partition which of course has to be unmounted before I can partition it. Also, as I have mentioned before, the bug is completely FS-independent.

> If you get problems while writing to the new filesystem...
I wish I HAD trouble WRITING to the file system because that would mean I could mount the drive. However I can't even do that due to some ATA commands being sent by some unknown application blocking the drive. Reducing the transfer buffer would only help if I could actually mount and use the drive (I did try it anyway and it didn't help as was to be expected)...

---

### Post by moviemaniac on 2010-01-31
> **kha said:**
> Hi,

I've searched all the day for my issue and it seems related to this topic also... Could you please confirm and explain me how it could be resolved ?

Hi!

I looked at your log and your problem seems to be an entirely different one and it has to do with the encryption as you mentioned.

Can you remove the partition in your virtual windows machine using the windows disk-manager thingy?

Another hint: Install Gparted and try to format the disk using that.

However if the drive uses hardware based encryption you might be out of luck because this prevents any access to the disk without prior authentication.

---

### Post by heldal on 2010-01-31
> **moviemaniac said:**
> Thanks, but the drive has been formatted correctly (on another machine because this bug prevents me from doing so on any computer running lucid...)


Look at this discussion in thread-mode and you'll see that my reply was directed at someone else's problem, not at all related to your problem.

> **moviemaniac said:**
> 
I wish I HAD trouble WRITING to the file system because that would mean I could mount the drive. However I can't even do that due to some ATA commands being sent by some unknown application blocking the drive. Reducing the transfer buffer would only help if I could actually mount and use the drive (I did try it anyway and it didn't help as was to be expected)...

I've noticed that. I've also noticed that people see a number of different errors in the logs. To summarise, it seems most USB mass-storage problems fall in one or more of the following categories.

1. buffer tuning

2. unhandled USB messages

3. timer issues


1 and 3 may be affected by small changes in kernel point-releases and probably fixed with tunable kernel/module parameters. Your problem (cat 2) may require more substantial changes to device-drivers or core parts of the usb-subsystem.

---

### Post by moviemaniac on 2010-01-31
> **heldal said:**
> Look at this discussion in thread-mode and you'll see that my reply was directed at someone else's problem, not at all related to your problem.

Oh, sorry. As you didn't quote anybody in particular I thought it was directed at the main issue being discussed in this topic. My bad.

---

### Post by kha on 2010-01-31
> **moviemaniac said:**
> Hi!
I looked at your log and your problem seems to be an entirely different one and it has to do with the encryption as you mentioned.

I've already tries that. The issue is that since the only disk mounted is /dev/sr1 and /dev/sdb is not accessible, GParted don't see anything and fdisk also gives me the error i already posted...

I am wondering if there is a way to zero-write the drive with dd for example, but i don't know which /dev/... to use to access directly the whole drive and destroy the first sectors.

On Windows, I can only remove and reformat the partition: the disk in not seen as one disk with two partitions (NTFS and UDF), but it is seen as two distinct disks, and the hidden encrypted partition is only seen and can only be formated after I unlocked the disk.

---

### Post by kha on 2010-01-31
I finally found the solution... Actually the Western Digital Portable Essential SE 1TB hard drive has a hardware encryption. When the disk is plugged, it creates two distinct drives (not two partitions): one read-only (UDF - cdrom) to install encryption tools and setup the other drive.

When you first plug the disk, It ask you to format it and prompt you for a password. Then, the only way to have the second disk seen is to unlock the drive. 

But I discovered today that you have then the option to disable password protection. This reformat the drive and let it being accessed as a normal usb drive even from Linux.

So I finally achieved to copy all my bootable linux distros (ubuntu, backtrack, slax, slitaz, ...) working with persistent changes onto !

Thank you !

---

### Post by moviemaniac on 2010-02-01
You beat me to it - I was just about to suggest looking for a way to disable encryption. I'm glad it's working again for you!

moviemaniac (who goes shopping for two new external enclosures not to get his two external drives to work again...)

---

### Post by thaitang on 2010-02-03
Hi Gang,

I am having trouble mounting usb pen drives as well as three external usb hard drives I use to keep all of my data on working between two laptops. I try to back up daily using Gsync to a pen drive for daily data changes, and weekly between external hard drives, but this has become a PITA since 2.6.31-17-generic. I just confirmed the pen drives and external drives mount fine if I boot to 2.6.31-16-generic or earlier (2.6.31-16-generic and 2.6.31-15-generic are all still in grub).

Any ideas if this is indeed a kernel bug? I have not found much while Googling for possible solutions, in fact this seems to be the most recent thread I found any kind regarding problems mounting external usb storage devices.

cheers,
tt

---

### Post by moviemaniac on 2010-02-03
I'm not sure. I've been only able to reproduce this *exact* bug on lucid with recent udev packages. My testing and the opinion of the upstream experts shows the kernel to not be the cause of this. You might very well encounter another bug. Could you post related errors from you /var/log/messages ?

---

### Post by b3t0n on 2010-02-27
I also have a problem with mounting external drives. When I connect my sansa mp3 player in MSC mode, it sometimes shows up in Computer, but when I click on the icon I can't mount it, it only offers safe removal. Lsusb recognises my player, so it isn't hardware fault. Player was mounting correctly until a week ago or something like that.

When I run nautilus as a root, and then try to mount player from the Computer it also doesn't offer that option. Still I can do it from the console with mount command, but it should be mounted automatically.

The device works correctly on my second PC and on Windows XP.
```
b3t0n@AspireONE:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0518:0005 EzKEY Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0781:74c1 SanDisk Corp. Sansa Fuze (msc)
Bus 001 Device 003: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by ttoms on 2010-02-28
I can't mount USB flash drives on two machines running lucid. Previously OK on Karmic, drives work fine on other PCs, so nothing wrong with them.

Drive listed as /dev/sdb1 so it's definitely there. Can't mount it though.

My current workaround is to plug in the drive as the system boots. It mounts fine then.

---

