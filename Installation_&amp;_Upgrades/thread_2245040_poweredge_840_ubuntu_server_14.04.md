---
title: "poweredge 840 ubuntu server 14.04"
date: 2014-09-20
forum: Installation &amp; Upgrades
---

### Post by scottie4442 on 2014-09-20
ok I have worked with Linux for years and installed Ubuntu server on several servers. That said I have been trying to install Ubuntu server 14.04 on a Poweredge 840. When it gets to the partition manager I have tried guided and it creates a partition called bootgrub, the rest of the partitions are ok but this will not boot. I am assuming this is supposed to be an uefi partition, this server is bios boot only.  I have tried everything I can think of to get this to boot with MBR but no luck so far. Any ideas would be helpful.  I have read over a 100 post trying to get this fixed but no luck so far.

---

### Post by tgalati4 on 2014-09-20
Is there RAID BIOS on the machine?  Try Control-S during boot.  Otherwise upgrade the BIOS from Dell to the latest.  If you are not using RAID on this server, then set the RAID BIOS to JBOD (just a bunch of disks).

---

