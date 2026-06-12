---
title: "Paritiions"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by McHenry on 2006-09-24
I am installing on a single 80gb SATA HDD

I select "Erase entire disk: SCSI1(0,0,0)(sda)" as opposed to the LVM option however it creates two partitions:
partition1 ext3
partition5 swap

My question is hat happened to partitions 2,3,& 4 or are they skipped for some reason ?

Thanks

---

### Post by pommattski on 2006-09-24
> **McHenry said:**
> ...My question is hat happened to partitions 2,3,& 4 or are they skipped for some reason ?

Basically; this is normal.

A physical drive can have up to 4 **primary** partitions, one of which can be an **extended** partition. Partition numbers 1, 2, 3 and 4 are reserved for these.
The **extended** partition can contain a number of **logical** partitions and can thus be thought of as a container for the logical partitions.
The first **logical** partition within the **extended** partition is always **5**.

Hope that is of some help...

---

