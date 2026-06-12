---
title: "Lacie Minimus USB3.0 mounted with only 10 MB size"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by pvanos on 2011-08-10
I yesterday bought a LaCie Minimus USB3.0 external HDD (1 TB size).
On my HP-laptop I'm currently running Ubuntu 2.6.32-33-generic.

After inserting the LaCie Minimus to a USB-connector, it is promptly detected, and correctly showing as "1,0 TB Hard Disk: LaCie"

In properties, however, it shows with a capacity of only 10 MB.
How can I mount it so that it shows its full capacity ?

Extract from "messages":
Aug 10 16:37:42 HPLAPTOP kernel: [10597.533003] usb 1-4: USB disconnect, address 7
Aug 10 16:37:57 HPLAPTOP kernel: [10612.632073] usb 1-4: new high speed USB device using ehci_hcd and address 8
Aug 10 16:37:58 HPLAPTOP kernel: [10612.773635] usb 1-4: configuration #1 chosen from 1 choice
Aug 10 16:37:58 HPLAPTOP kernel: [10612.774087] scsi8 : SCSI emulation for USB Mass Storage devices
Aug 10 16:38:03 HPLAPTOP kernel: [10618.349412] scsi 8:0:0:0: Direct-Access     ST310005 20AS             CC32 PQ: 0 ANSI: 0
Aug 10 16:38:03 HPLAPTOP kernel: [10618.350527] sd 8:0:0:0: Attached scsi generic sg2 type 0
Aug 10 16:38:03 HPLAPTOP kernel: [10618.351720] sd 8:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Aug 10 16:38:03 HPLAPTOP kernel: [10618.357319] sd 8:0:0:0: [sdb] Write Protect is off
Aug 10 16:38:03 HPLAPTOP kernel: [10618.360157]  sdb: sdb1
Aug 10 16:38:03 HPLAPTOP kernel: [10618.392846] sd 8:0:0:0: [sdb] Attached SCSI disk
Aug 10 16:38:03 HPLAPTOP kernel: [10618.478710] sd 8:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
Aug 10 16:38:03 HPLAPTOP kernel: [10618.478723] Descriptor sense data with sense descriptors (in hex):
Aug 10 16:38:03 HPLAPTOP kernel: [10618.478728]         72 01 04 1d 00 00 00 0a 09 0c 00 00 00 00 00 07 
Aug 10 16:38:03 HPLAPTOP kernel: [10618.478751]         00 00 
Aug 10 16:38:03 HPLAPTOP kernel: [10618.478758] sd 8:0:0:0: [sdb] ASC=0x4 ASCQ=0x1d
Aug 10 16:38:34 HPLAPTOP kernel: [10648.709338] sd 8:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
Aug 10 16:38:34 HPLAPTOP kernel: [10648.709350] Descriptor sense data with sense descriptors (in hex):
Aug 10 16:38:34 HPLAPTOP kernel: [10648.709356]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 87 
Aug 10 16:38:34 HPLAPTOP kernel: [10648.709379]         00 61 00 09 40 50 
Aug 10 16:38:34 HPLAPTOP kernel: [10648.709390] sd 8:0:0:0: [sdb] ASC=0x4 ASCQ=0x1d
Aug 10 16:38:34 HPLAPTOP kernel: [10648.870341] sd 8:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
Aug 10 16:38:34 HPLAPTOP kernel: [10648.870355] Descriptor sense data with sense descriptors (in hex):
Aug 10 16:38:34 HPLAPTOP kernel: [10648.870360]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
Aug 10 16:38:34 HPLAPTOP kernel: [10648.870383]         00 4f 00 c2 40 50 
Aug 10 16:38:34 HPLAPTOP kernel: [10648.870395] sd 8:0:0:0: [sdb] ASC=0x4 ASCQ=0x1d

---

### Post by pvanos on 2011-08-11
I found the solution : (via Ubuntu software center) download and install gparted.
From a terminal : sudo gparted
Then select the correct drive (in my case: /dev/sdb )
Most of the space was unallocated. I deleted the 2 small existing partitions, and created a new partition table, and then a new partition. I selected an EXT3 partition.
Resulting in a capacity of 916,9 GB, 46,8 GB used (??) and 870,1 GB free.

---

