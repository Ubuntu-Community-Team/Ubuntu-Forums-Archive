---
title: "Cannot boot up with 2.6.31 kernel after upgrade from 9.04"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scottmuz on 2009-10-24
Did an upgrade last night from Jaunty to Karmic.

I can't boot up with th 2.6.31 kernel.
But I can boot up into Karmic with the 2.6.28 kernel.

Using amd64 architecture.

I get the following error message when I boot up with 2.6.31
"Mount of root filesystem failed" 
and then I drop into the maintenance shell.

---

### Post by scottmuz on 2009-10-24
Solved.

My fstab didn't work in 2.6.31. It didn't work with options
  defaults,data=writeback,noatime,barrier=0,extents,journal_checksum
and worked fine when I changed them to
  errors=remount-ro,noatime,relatime,nodiratime

---

