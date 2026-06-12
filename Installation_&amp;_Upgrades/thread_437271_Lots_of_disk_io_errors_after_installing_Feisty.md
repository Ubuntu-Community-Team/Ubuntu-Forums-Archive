---
title: "Lots of disk io errors after installing Feisty"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by finalzero on 2007-05-08
Hi,

I have noticed dozens of the following messages in my syslog:

```
May  5 23:50:04 gamma kernel: [    3.793980]  unknown partition table
May  5 23:50:04 gamma kernel: [    3.794174] sd 2:0:1:0: Attached scsi disk sdb
May  5 23:50:04 gamma kernel: [    3.799614] sd 2:0:0:0: Attached scsi generic sg0 type 0
May  5 23:50:04 gamma kernel: [    3.799694] sd 2:0:1:0: Attached scsi generic sg1 type 0
May  5 23:50:04 gamma kernel: [    3.875154] attempt to access beyond end of device
May  5 23:50:04 gamma kernel: [    3.875221] sda: rw=0, want=573440031, limit=321672960
May  5 23:50:04 gamma kernel: [    3.875283] Buffer I/O error on device sda2, logical block 51199136
May  5 23:50:04 gamma kernel: [    3.876160] attempt to access beyond end of device
May  5 23:50:04 gamma kernel: [    3.876215] sda: rw=0, want=573440031, limit=321672960
May  5 23:50:04 gamma kernel: [    3.876269] Buffer I/O error on device sda2, logical block 51199136
May  5 23:50:04 gamma kernel: [    3.876350] attempt to access beyond end of device
May  5 23:50:04 gamma kernel: [    3.876406] sda: rw=0, want=573440175, limit=321672960
May  5 23:50:04 gamma kernel: [    3.876463] Buffer I/O error on device sda2, logical block 51199154
May  5 23:50:04 gamma kernel: [    3.876492] attempt to access beyond end of device
May  5 23:50:04 gamma kernel: [    3.876499] sda: rw=0, want=643338800, limit=321672960
May  5 23:50:04 gamma kernel: [    3.876504] Buffer I/O error on device sda3, logical block 69898624
May  5 23:50:04 gamma kernel: [    3.876514] attempt to access beyond end of device
May  5 23:50:04 gamma kernel: [    3.876519] sda: rw=0, want=643338801, limit=321672960
May  5 23:50:04 gamma kernel: [    3.876522] Buffer I/O error on device sda3, logical block 69898625
May  5 23:50:04 gamma kernel: [    3.876531] attempt to access beyond end of device
May  5 23:50:04 gamma kernel: [    3.876536] sda: rw=0, want=643338802, limit=321672960
May  5 23:50:04 gamma kernel: [    3.876540] Buffer I/O error on device sda3, logical block 69898626
May  5 23:50:04 gamma kernel: [    3.876548] attempt to access beyond end of device
```

My disk is configured as follows:

NTFS (Partition 1 Primary)
NTFS LOGICAL
     ---> Partition 4
     ---> Partition 5
     ---> Partition 6
     ---> Partition 7
     ---> Partition 8 (FAT32 shared)
EXT3 Ubuntu (Partition 2 Primary)
LINUX-SWAP (Partition 3 Primary)

The above is configured on the boot drive, I then have three more drives setup in RAID0+1 which are only accessible by Windows XP.

I have never had any issues in Ubuntu 6.10 Edgy however I have noticed the above messages time and again since installing 7.04 Feisty.

I can only come to the conclusion 7.04 is a seriously buggy release, the disk management is flawed hence the partitions are not setup correctly, peoples drives go missing during grub boot and I get the above errors.  Anyone know of a simple fix or even how to ditch the whole scsi stuff and use Ubuntu 6.10's way of treating disks i.e. reading IDE drives as IDE drives and not sata/scsi?

Thanks,

Fz

---

