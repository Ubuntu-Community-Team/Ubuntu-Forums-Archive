---
title: "Jfs"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by syzhang on 2011-08-01
I'm just wondering if Ubuntu supports JFS. I have a partition, which is JFS type but unfortunately, I didn't create a lvm for it. Is there any method that can create a lvm and mount the JFS on it without deleting any data on that partition? Thanks a lot!

---

### Post by karlson on 2011-08-01
> **syzhang said:**
> I'm just wondering if Ubuntu supports JFS. I have a partition, which is JFS type but unfortunately, I didn't create a lvm for it. Is there any method that can create a lvm and mount the JFS on it without deleting any data on that partition? Thanks a lot!

have you tried
```

sudo modprobe jfs

```

---

