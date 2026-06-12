---
title: "Problem accessing RAID volume"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by lauluisa on 2012-02-20
Hi.

Firm where I work used to have RedHat 8 server with 2 HDD-s in RAID. Now Ubuntu 10 has been installed on one HDD, the other shows as array, but is not started. Disk tool shows 2 RAID partitions. When I try starting it I get the "not enough components" message. I do not know which RAID was used. Is it somehow possible to access that volume?

---

### Post by mayavi2011 on 2012-02-20
> **lauluisa said:**
> Hi.

Firm where I work used to have RedHat 8 server with 2 HDD-s in RAID. Now Ubuntu 10 has been installed on one HDD, the other shows as array, but is not started. Disk tool shows 2 RAID partitions. When I try starting it I get the "not enough components" message. I do not know which RAID was used. Is it somehow possible to access that volume?

Yes it is; I just rescued my RAID data using PMagic-2011-12-30-X86-64
:-)

---

### Post by lauluisa on 2012-02-20
OK, I used mdadm and can now mount the RAID partition just fine. Unfortunately there are user rights there, as it was a server and now I have to somehow override those :(

---

