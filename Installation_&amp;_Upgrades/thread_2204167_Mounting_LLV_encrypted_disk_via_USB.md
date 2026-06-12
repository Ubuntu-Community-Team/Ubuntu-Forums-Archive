---
title: "Mounting LLV encrypted disk via USB"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by dargaud2 on 2014-02-07
Hello all,
I'm in the process of upgrading.
I just installed the latest Kubuntu to a new disk. I've removed the old disk and put it in an external USB enclosure. Now I'm simply trying to mount it so I can copy my files over but the partition on it is encrypted (via the previous ubuntu installer). It's /dev/sdb. I tried the following:
```
$ sudo cryptsetup luksOpen /dev/sdb secure
$ sudo mount /dev/mapper/secure /mnt
mount: special device /dev/mapper/secure does not exist
```
Could it be that there's something wrong with my external USB adapter ?
```
$ dmesg
[  318.190738] usb 2-1.2: new high-speed USB device number 8 using ehci-pci
[  318.285820] usb 2-1.2: New USB device found, idVendor=152d, idProduct=2338
[  318.285826] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[  318.285830] usb 2-1.2: Product: USB to ATA/ATAPI Bridge
[  318.285833] usb 2-1.2: Manufacturer: JMicron
[  318.285836] usb 2-1.2: SerialNumber: 152D203380B6
[  318.287441] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[  318.287594] scsi7 : usb-storage 2-1.2:1.0
[  319.288516] scsi 7:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[  319.288960] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  319.292286] sd 7:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  319.294712] sd 7:0:0:0: [sdb] Asking for cache data failed
[  319.294721] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  319.298324] sd 7:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  319.300056] sd 7:0:0:0: [sdb] Asking for cache data failed
[  319.300060] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  319.300063] sd 7:0:0:0: [sdb] Attached SCSI disk
```

---

### Post by dargaud2 on 2014-02-07
OK, the Sata to USB adapter was bad. I used another one and it asked for the passwd and mounted without difficulty.

---

