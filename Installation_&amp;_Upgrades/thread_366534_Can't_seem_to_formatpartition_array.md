---
title: "Can't seem to format/partition array"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by AndyInNYC on 2007-02-21
I have a 1.2 TB array attached to a 3ware card (6 x 250 GB drives).  The drive is seen correctly under 6.06, but I am using 6.1 due to other problems.

Under 6.1 I installed gparted and psydm.

gparted, however, sees the drive as being -948739569152.00 in size.  Is this a roll-over problem in gparted?  Is there a better/different tool I should use?  Golly I miss disk manager in 6.06.

How do I partition and format the drive and then get it correctly mounted?

Andrew

---

### Post by dcstar on 2007-02-21
> **AndyInNYC said:**
> I have a 1.2 TB array attached to a 3ware card (6 x 250 GB drives).  The drive is seen correctly under 6.06, but I am using 6.1 due to other problems.

Under 6.1 I installed gparted and psydm.

gparted, however, sees the drive as being -948739569152.00 in size.  Is this a roll-over problem in gparted?  Is there a better/different tool I should use?  Golly I miss disk manager in 6.06.

How do I partition and format the drive and then get it correctly mounted?

Andrew

Install the **pysdm** package and then you may be able to use the new System-Administration-Storage Device Manager menu item to mount it (not sure about the format though).

---

### Post by AndyInNYC on 2007-02-21
pysdm won't see anything more than sdc until the drive is partitioned.

Is there a partition tool that runs under 6.1 which will correctly see the size of a 1.2 TB drive?

Anyone?

Andrew

---

