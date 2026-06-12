---
title: "Hardy: How do I get a UUID for a moved /var partition"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2008-09-17
Hi,
My Kubuntu Hardy 3.9 GB ext3 / partition got full.
In order to solve the problem, I've decided to create a new partition (at the "expense" of my current /home separate partition) and move var (currently under my / in the same partition) to the that new partition.
I'll be using Knoppix.
Naturally, I'll have to edit my fstab to reflect the change, yet I don't know how to get the UUID for my new /var partition (or can I add a new entry in the fstab  WITHOUT a UUID??).
Please advise!

Thanks

Michael Badt

---

### Post by iaculallad on 2008-09-17
You can get your UUID by issuing the command below on your terminal:

```
sudo blkid
```

EDIT:

You could also use:

```
ls -l /dev/disk/by-uuid
```

---

### Post by mibadt on 2008-09-17
That was FAST!

Thanks a lot !!:)

Michael Badt

---

