---
title: "Can't install on IDE hard drive, solved"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by germsteel on 2008-05-15
ECS 945GCT-M v.3, E2200, Crucial 1GB x 2 DDR2 PC6400 RAM.
This board has a REALTEK 8101E that wasn't working with SUSE 10 SP1.  I didn't want to compile a new driver etc. etc.

IDE HD & DVD drive.  Maxtor 20GB pulled from an Apple Cube that I upgraded and an Emprex DVD R/W.

So I turned to Hearty Heron, joy the network is working fine but installation stops 47% way through the copy files and says it can't copy.  Then it kept messing up the pre-existing partitions.
It also showed my IDE drive to be a SCSI.


Work around:
In the BIOS
Disable SATA controller.  Disable all other IDE device entries make sure DVD and HD are the only ones showing and their SLAVE / MASTER status is correct.  I used my DVD as primary Master and the HD as primary Slave.

Turn off legacy USB support I read that somewhere.  And then I used whole drive partition.  

It worked!

---

