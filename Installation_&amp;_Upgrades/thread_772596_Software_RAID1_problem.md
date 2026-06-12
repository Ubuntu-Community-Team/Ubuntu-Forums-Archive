---
title: "Software RAID1 problem"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Trebaruna on 2008-04-28
I'm trying to get Ubuntu 8.04 to setup a RAID1 array between two disks. I've been following [this guide]("http://users.piuha.net/martti/comp/ubuntu/en/raid.html") to try and get it to work, but whenever I get to the configure software RAID stage and select create MD device it tells me there are no unused raid autodetect partitions.
Instead, it makes one large RAID device, which I can format as one partition. Trying to make a smaller partition results in the rest of the space being labeled "unusable".
I'm using an MSI K9AGM3-F board (ATi SB600 southbridge) and two SATA drives. The SATA controller is configured as "AHCI", no fakeRAID here.

Any help?

---

