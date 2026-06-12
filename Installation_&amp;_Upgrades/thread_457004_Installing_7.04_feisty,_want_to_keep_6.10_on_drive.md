---
title: "Installing 7.04 feisty, want to keep 6.10 on drive"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by timcredible on 2007-05-28
I have the following partitions:

hda1 - ubuntu 6.06 system 
hda2 - ubuntu 6.10 system
hda3 - swap
hda4 - /home

I want to install feisty on hda1 and keep edgy as-is (I like to do this so I can still boot into 6.10 for a while until I have 7.04 completely ready).  So, I want this:

hda1 - ubuntu 7.04 system
hda2 - ubuntu 6.10 system
hda3 - swap
hda4 - /home

But, the new installer, when using custom partitioning, the only choice is to edit partitions, and I don't want to change the partitions, I just want to define what the mount points for them should be.  

Does anyone know if the partitioner will actually re-write the partition table if all I do is change the mount point?  And why isn't there a "use existing partitions" option?

Thanks.

---

### Post by Pumalite on 2007-05-28
> **timcredible said:**
> I have the following partitions:

hda1 - ubuntu 6.06 system 
hda2 - ubuntu 6.10 system
hda3 - swap
hda4 - /home

I want to install feisty on hda1 and keep edgy as-is (I like to do this so I can still boot into 6.10 for a while until I have 7.04 completely ready).  So, I want this:

hda1 - ubuntu 7.04 system
hda2 - ubuntu 6.10 system
hda3 - swap
hda4 - /home

But, the new installer, when using custom partitioning, the only choice is to edit partitions, and I don't want to change the partitions, I just want to define what the mount points for them should be.  

Does anyone know if the partitioner will actually re-write the partition table if all I do is change the mount point?  And why isn't there a "use existing partitions" option?

Thanks.

Stay with 6.10 We are having nothing but trouble here. Wait until 7.04 is stable.

---

### Post by timcredible on 2007-05-29
So, 7.04's installer will not allow me to just use existing partitions?  That stinks.   Who decided to take that option out?  I would like to stay with ubuntu, but i'm not re-creating my home directory every time i want to upgrade - I guess I'll go back to pclos.

---

