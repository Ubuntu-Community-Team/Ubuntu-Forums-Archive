---
title: "leaving empty spaces between partitions"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2007-01-11
Is there any benefit or negative issues to leaving a small unallocated disk space between the swap, root and home partitions ?

Thanks.

---

### Post by meng on 2007-01-11
I can't see any advantage to this, an expert mnight know differently though. Certainly there's the disadvantage of wasting space. You're better off having one contiguous unallocated space than several small non-contiguous ones.

---

### Post by wpshooter on 2007-01-11
The reason I ask is because this ability is provided for in the partitioning software in Ubuntu/Linux.  If there was no purpose to this, why would the parameter be provided to allow you to put an amount of space prior to a partition ?

Thanks.

---

### Post by meng on 2007-01-11
You have the option of leaving unallocated space wherever you like. But there's no advantage to having several small unallocated spaces which are not contiguous.

---

### Post by PurplePenguin on 2007-01-11
> **wpshooter said:**
>  If there was no purpose to this, why would the parameter be provided to allow you to put an amount of space prior to a partition ?

In case you want to make another partition before that one. :)

---

