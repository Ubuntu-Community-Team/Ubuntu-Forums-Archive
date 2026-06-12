---
title: "Logical partitions are default ?"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by randysparks on 2008-05-21
I seems that in Hardy Ubuntu automatically creates a new logical partition for the root and swap, after it's shrunk the Windows partition. 

Is this default behaviour?

---

### Post by forestpixie on 2008-05-21
I believe it is - the logic I assume being that you can only have 4 primary partitions, including extended partitions. AS buntu will install to logical partitions it makes sense to not use 2 seperate primary partitions to achieve the aim.

---

### Post by randysparks on 2008-05-21
> **forestpixie said:**
> I believe it is - the logic I assume being that you can only have 4 primary partitions, including extended partitions. AS buntu will install to logical partitions it makes sense to not use 2 seperate primary partitions to achieve the aim.

I guess it does no harm, but the problem is that the root partition is now typically numbered 5 in fdisk -l (and 0,4 in GRUB), on a dual-boot system, which screws up a lot of instructions out there on how to do stuff under Ubuntu, and also confuses newbies a little. It took me a minute or two to work out what was going on. 

But thanks for the help.

---

### Post by zvacet on 2008-05-21
Ubuntu will install on primary and logical partition with same result.So,that is no problem.Why is your root on hda5 doesn´t depend of partition type.It depends of what is installed before Ubuntu.

---

