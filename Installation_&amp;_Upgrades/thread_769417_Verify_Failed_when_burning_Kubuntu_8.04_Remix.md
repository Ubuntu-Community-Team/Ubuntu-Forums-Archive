---
title: "Verify Failed when burning Kubuntu 8.04 Remix"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by jorwex on 2008-04-26
I've tried burning it twice. Second time I did it the slowest my burner would let me. Both times I left the PC alone. I'm running Ubuntu 7.10. I'll try Brasero while you friendly people reply. 

[img]http://glue.umd.edu/~jwexler/kde.png[/img]

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-16-generic
Devices
-----------------------
_NEC DVD_RW ND-3500AG 2.19 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite]

K3bDataTrackReader
-----------------------
reading sectors 0 to 352927 with sector size 2048. Length: 352928 sectors, 722796544 bytes.
using buffer size of 64 blocks.
Read a total of 352928 sectors (722796544 bytes)

K3bMd5Job
-----------------------
Reached max read of 722796544. Stopping after 722796544 bytes.

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : '_NEC    '
Identification : 'DVD_RW ND-3500AG'
Revision       : '2.19'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 1343488 = 1312 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1411 KB/s
Track 01: data   689 MB        
Total size:      791 MB (78:25.70) = 352928 sectors
Lout start:      791 MB (78:27/53) = 352928 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 6918
Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  689 MB written.
Track 01:    1 of  689 MB written (fifo  99%) [buf 100%]  63.0x.
Track 01:    2 of  689 MB written (fifo 100%) [buf 100%]   0.4x.
......<OMITTED BECAUSE OF REPETITION>.....
Track 01: Total bytes read/written: 722796544/722796544 (352928 sectors).
Writing  time:  616.380s
Average write speed   7.8x.
Min drive buffer fill was 100%
Fixating...
Fixating time:   20.749s
BURN-Free was never needed.
/usr/bin/wodim: fifo had 11385 puts and 11385 gets.
/usr/bin/wodim: fifo was 0 times empty and 11181 times full, min fill was 95%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=8 -dao driveropts=burnfree -eject -data -tsize=352928s - 
```

---

### Post by Pumalite on 2008-04-26
Do md5sum on the iso before burn. Clean the lens in you burner.

---

### Post by jorwex on 2008-04-26
md5sums match. lens clean the burner? really? I'm very particular about cd cleanliness. I haven't had this problem yet. I just finished burning 8.04 ubuntu no problems. i'll try different media maybe.

any other suggestions?

---

### Post by Pumalite on 2008-04-26
Burn at 4x or less, use CD-R of good quality.

---

### Post by jorwex on 2008-04-26
im trying my roommate's imation right now. k3b doesnt let me burn less than 8x

---

### Post by jorwex on 2008-04-26
different media failed still :(

---

### Post by Odur on 2008-05-01
I've got the same problem on all my DVD burns. It started with Hardy, and there where no problem in Gutsy. At first I thought it was my burner (IDE), so I bought a new one (SATA) but no luck. The verify process go to 100% and then I get exactly the same message as above. All the burns is playing very well in spite of the error, so I don't verify anymore. It's probably a bug in k3b or in the backend.

---

### Post by rbeem on 2008-05-15
I'm having the same problem.  Gutsy worked fine and Hardy fails on every DVD burn on both my SATA and USB burners.  CDs have verified successfully.

---

### Post by jorwex on 2008-05-16
I don't want to be rude, but that's not the same problem. My CD's work fine but they don't verify.

---

