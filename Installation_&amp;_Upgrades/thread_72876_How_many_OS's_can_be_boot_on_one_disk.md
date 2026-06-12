---
title: "How many OS's can be boot on one disk?"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by vayu on 2005-10-07
I read somewhere that the 512 byte boot sector has a limit of 4 primary partitions.  That would lead me to think that you could boot between 4 different OS's.  But somewhere else I read that the extended partition that houses the logical partitions is also a primary partition, so I think that would mean 3 OS's.
Anybody know?

---

### Post by Dennis Laumen on 2005-10-07
You can install Operating Systems on both Primary and Logical partitions. You can only have four primary partitions but the number of Logical partitions you can have are "unlimited" (of course if you have the space to house that many partitions).

One warning though, Windows can not be installed in a Logical partition. That is the only exception I know.

---

