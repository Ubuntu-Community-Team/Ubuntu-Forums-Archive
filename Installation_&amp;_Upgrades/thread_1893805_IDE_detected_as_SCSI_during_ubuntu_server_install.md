---
title: "IDE detected as SCSI during ubuntu server install"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by fedtobunt on 2011-12-11
Hi,
I am installing Ubuntu server 11.10 64bit and my IDE drive is being detected as SCSI during partitioning step? How to fix? or is this normal?

SCSI (0,0,0) sda - 40.0GB ATA ST340026A

---

### Post by dino99 on 2011-12-11
First go to the bios settings to know about ahci/ide/compatible choice made

---

### Post by fedtobunt on 2011-12-11
> **dino99 said:**
> First go to the bios settings to know about ahci/ide/compatible choice made
Choices were ide/ahci/RAID
selcted with AhCI would not boot from the SATA DVD rom. 
I set it to IDE.
but these are for SATA ports. No such setting for IDE.
The HDD is a PATA drive connected as master.

---

### Post by darkod on 2011-12-11
Yes, it's normal. Earlier the PATA disks were called hd? and the SATA sd? but since few years ago all disks are called sd?.

Don't worry, just go on.

---

### Post by fedtobunt on 2011-12-11
> **darkod said:**
> Yes, it's normal. Earlier the PATA disks were called hd? and the SATA sd? but since few years ago all disks are called sd?.

Don't worry, just go on.

Ok. but it still saying SCSI not just id of /dev/sda.
Anyway I'll continue on with the install.

---

