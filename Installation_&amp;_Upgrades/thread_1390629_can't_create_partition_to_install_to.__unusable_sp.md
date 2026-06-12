---
title: "can't create partition to install to.  unusable space."
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by Bakon Jarser on 2010-01-25
When I boot the ubuntu live cd (9.10) and attempt to install it only gives two options at the partitioning screen.  One is to use the whole disk and the other is to manualy assign partitions.  I told it to resize one of my partitions and created 18GB of free space.  However, it tells me this space is "unusable".  It wouldn't let me do anything with it and I used windows vista disk manager to add it back to the original partition. I have one hard drive with four partitions.  One is a restore partition, one windows partition, one storage partition, and one that says xp although i don't have xp installed.  It might be used by the acer restore program.  It's an acer aspire 6920.

---

### Post by Leppie on 2010-01-25
> **Bakon Jarser said:**
> When I boot the ubuntu live cd (9.10) and attempt to install it only gives two options at the partitioning screen.  One is to use the whole disk and the other is to manualy assign partitions.  I told it to resize one of my partitions and created 18GB of free space.  However, it tells me this space is "unusable".  It wouldn't let me do anything with it and I used windows vista disk manager to add it back to the original partition. I have one hard drive with four partitions.  One is a restore partition, one windows partition, one storage partition, and one that says xp although i don't have xp installed.  It might be used by the acer restore program.  It's an acer aspire 6920.
my guess is that you have 4 primary partitions assigned, which is also the maximum. so creating free space would not make it possible to use it for an additional partition.
the only thing you could do is make a backup of one of the partitions, then delete it and create an extended partition (which is also a primary partition but can hold several logical partitions) and restore the backup to a logical partition.

---

### Post by oldos2er on 2010-01-25
If you have four primary partitions, then you wouldn't be able to create any more. You'll need to delete one, then you can create an extended partition containing as many logical partitions as you need.

---

