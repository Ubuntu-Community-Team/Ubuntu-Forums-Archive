---
title: "Ubuntu 6.06 Server on Dell PowerEdge SC1420"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by orlando_tg on 2006-07-10
I've just configure the RAID controller to do a RAID1 with 2 SATA HDD 80GB each, but when I'm installing Ubuntu Server 6.06 at partitioning fase, the HDD's appears individuals, not as RAID1 volume (sda, sdb)...???

Any suggestion?

Thanks a lot :-k

---

### Post by ... on 2006-07-15
There is a decent chance that the raid card you got isn't really a raid card, but just sata controller with some software that does the raid. Looking at the dell site the only hardware raid controller is the PERC U320, which is a scsi one, so that is probably the case... 

I would just configure a software raid with the ubuntu, the installer makes it pretty easy ;)

---

