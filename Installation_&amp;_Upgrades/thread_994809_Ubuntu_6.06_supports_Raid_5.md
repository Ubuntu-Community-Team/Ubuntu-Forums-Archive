---
title: "Ubuntu 6.06 supports Raid 5"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by kieranchiru on 2008-11-27
Hi All, :)

I wud like to know Ubuntu Operating system supports Raid 5 and backup drive.


Cheers
Kieran

---

### Post by heimo on 2008-11-27
> **kieranchiru said:**
> Hi All, :)

I wud like to know Ubuntu Operating system supports Raid 5 and backup drive.


Hi - I'm pretty sure 6.06 does support RAID5. But then, there are many kind of ways to implement RAID (hardware/software/"fake-raid"). True hardware solutions will work, most of the cheap integrated RAID-functions on motherboards and some cards which are fake-raid, should probably be avoided and instead a pure software raid could be used.

Some information here:
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

Notice that it's not possible to boot from software RAID5 and you'll need non-raid or perhaps RAID1 for your boot partition.

---

