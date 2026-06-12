---
title: "Ubuntu 7.04 on Dell Inspiron 2650: thinks hdd is SCSI?"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by gravyface on 2007-09-20
Running live CD for ubuntu 7.04 and seems to work fine installing up until the point where I need to choose my partitions/hdds etc.  No matter what I try, it thinks the Hitachi 30GB drive is SCSI?  Xubuntu Edgy worked fine; had no issues seeing it, but Damn Small Linux (latest as of Sept.) had init issues on a SCSI-related probing, and it's also Debian-like I believe, so perhaps it's something with the latest kernel?  Can't get the 3COM wireless adapter to work on Edgy so I was hoping the latest would help but now, it's another issue.

---

### Post by Pumalite on 2007-09-20
Post your specs. You might need Alternate CD.

---

### Post by gravyface on 2007-09-20
Dell Computer Corporation Inspiron 2650 Revision A0
1.70 gigahertz Intel Pentium 4 Mobile
256 Megabytes Installed Memory
8 kilobyte primary memory cache
512 kilobyte secondary memory cache
Bus Clock: 100 megahertz
BIOS: PHOENIX TECHNOLOGIES LTD. A03 06/04/2002

HL-DT-ST RW/DVD GCC-4240N [CD-ROM drive]
3.5" format removeable media [Floppy drive]

HITACHI_DK23DA-30 [Hard drive] (30.00 GB) -- drive 0, s/n 130M41, rev 00J1A0G2

Standard floppy disk controller
Intel(R) 82801CAM Ultra ATA Storage Controller-248A
Primary IDE Channel [Controller]
Secondary IDE Channel [Controller] 
NVIDIA GeForce2 Go [Display adapter]

O2Micro OZ6912 CardBus Controller
Intel(R) 82801CA/CAM USB Universal Host Controller - 2482
Intel(R) 82801CA/CAM USB Universal Host Controller - 2484

Com 3C920 Integrated Fast Ethernet Controller (3C905C-TX Compatible)
3Com 3CRWE62092B Wireless LAN PC Card

---

### Post by Pumalite on 2007-09-20
With that RAM I would go for Xubuntu Alternate CD for a fast system: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
You could boot and even install Live CD if you make a 1 GB swap partition ahead of time, but I think the system would be sluggish with your amount of RAM.

---

