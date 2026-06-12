---
title: "[SOLVED] Problem using Remastersys on a SATA HDD"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by teejcee on 2008-07-11
I'm experiencing a problem when I try to use Remastersys to clone my Hardy Heron system onto a sata hdd.
The system I've cloned was itself cloned from another box onto an 80gb ide hdd, but as this drive is a bit old & making some strange noises, so I decided to move it to the sata.

Everything works fine up until the partitioner starts... it shows 5% complete and after a few minutes the entire system locks up...mouse, keyboard are inoperable.

I've tried the original dvd that I used for the ide & the same thing happens.

As an experiment to determine if it is Ubuntu related, I've tried to partition this sata drive using gparted and the same thing happens.

I've also tried running gparted against the drive from a Knoppix live-cd and it works fine, so it looks to be an Ubuntu problem.

Here's some information that may be asked for....

Motherboard   Aopen AK79G Max with onboard Promise SATA150
HDD           Western Digital  WD500AAKS  500GB

```
sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23eb3fd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60044   482303398+  83  Linux
/dev/sda2           60045       60801     6080602+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa51aa51a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xccecccec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30400   244187968+   7  HPFS/NTFS
```


```
 dmesg | grep ata
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[   27.987686] Memory: 2066804k/2097088k available (2177k kernel code, 29032k reserved, 1006k data, 368k init, 1179584k highmem)
[   27.987710]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   33.933087] libata version 3.00 loaded.
[   34.698866] sata_promise 0000:01:0b.0: version 2.11
[   34.714499] scsi0 : sata_promise
[   34.715938] scsi1 : sata_promise
[   34.717384] scsi2 : sata_promise
[   34.717474] ata1: SATA max UDMA/133 mmio m4096@0xd7020000 port 0xd7020200 irq 19
[   34.717481] ata2: SATA max UDMA/133 mmio m4096@0xd7020000 port 0xd7020280 irq 19
[   34.717485] ata3: PATA max UDMA/133 mmio m4096@0xd7020000 port 0xd7020300 irq 19
[   35.183719] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   35.192148] ata1.00: ATA-8: WDC WD5000AAKS-65YGA0, 12.01C02, max UDMA/133
[   35.192156] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   35.208151] ata1.00: configured for UDMA/133
[   35.519252] ata2: SATA link down (SStatus 0 SControl 0)
[   35.676958] pata_amd 0000:00:09.0: version 0.3.10
[   35.678597] scsi3 : pata_amd
[   35.679408] scsi4 : pata_amd
[   35.680697] ata4: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   35.680703] ata5: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   35.804976]  sda: sda1 sda2 <<6>ata4.00: ATA-6: WDC WD800JB-00ETA0, 77.07W77, max UDMA/100
[   35.852198] ata4.00: 156301488 sectors, multi 16: LBA48 
[   35.861920] ata4.01: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
[   35.861928] ata4.01: 488397168 sectors, multi 16: LBA48 
[   35.876165] ata4.00: configured for UDMA/100
[   35.883292] ata4.01: configured for UDMA/100
[   36.366762] ata5.00: ATAPI: SAMSUNG CD-R/RW SW-252B, R701, max UDMA/33
[   36.366796] ata5.01: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A103, max UDMA/33
[   36.538485] ata5.00: configured for UDMA/33
[   36.710160] ata5.01: configured for UDMA/33
[   37.255301] EXT3-fs: mounted filesystem with ordered data mode.

```
Any help would be greatly appreciated.

---

### Post by teejcee on 2008-07-14
bump....

---

### Post by teejcee on 2008-07-16
bump, bump....Looks like I'm drawing a blank here.

I guess one option is to get a new ide drive ( which I know will work ) & move on.

---

### Post by VMC on 2008-07-16
Does that Remastered Livecd have Media check option on the first page? If so check the media first. Maybe just a bad burn. Maybe I've mis-read your problem.

---

### Post by teejcee on 2008-07-16
Yep..both DVDs used have had the media check ran against them..both ok.

I've now found that the Promise sata controller is a PDC20375

Also the kernel module is listed as ...
"sata_promise       Promise ATA TX2/TX4/TX4000 low-level driver" ,
"Version Magic      2.6.24-19-generic SMP mod_unload 586"   libata is also loaded.

I don't know what else I can post to enable others to perhaps solve this issue.

Thanks for the input VMC....  'helps keep the thread alive.

---

### Post by teejcee on 2008-07-18
I'm not sure if I can mark this thread as completely solved, however, I have been able to at least install my cloned Ubuntu via Remastersys onto my sata hdd.

Using Gparted, I removed all partitions from the disk and then added a partition with the minimum size of 8mb, then did the installation from the dvd with the cloned system.

I have no idea why this enables the installation to succeed and I now have an 8mb "Media" drive mounted when I boot, which I'd like to get rid of but if it's the only way to get around my original problem, I'm sure I can live with it.

Can anyone explain this??

---

### Post by teejcee on 2008-07-19
Having had no replies, I have reverted to the age old tradition of "trial-and-error"..

I used gparted to flag the extended partition as boot, deleted the 8mb partition and re-booted...

All is well...the 8mb media drive is gone..!

I really have no idea if what I've done is the correct approach & even less idea as to why I had to take all these steps but as everything is now working to my satisfaction I guess I can flag this as SOLVED.

---

