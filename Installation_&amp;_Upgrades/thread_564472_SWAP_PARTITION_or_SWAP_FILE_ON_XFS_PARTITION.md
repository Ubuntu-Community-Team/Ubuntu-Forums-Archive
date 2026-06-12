---
title: "SWAP PARTITION or SWAP FILE ON XFS PARTITION"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by justin_nita on 2007-10-01
_The fastest_: SWAP PARTITION or SWAP FILE ON XFS PARTITION?

In some operations XFS is faster. Those operations perfectly fit to me. So, if I set the main partition to XFS and the swap to be a file on XFS main partition, it would be faster than a XFS main partition and a separated swap partition?

curiosity: there are different types of swap partitions depending on main partition type (ex. XFS, EXT3)?


:confused:

---

### Post by az on 2007-10-01
A swap partition has no filesystem, and therefore has one less layer of abstraction.  A swap partition should be the fastest, given the two choices.

---

### Post by justin_nita on 2007-10-01
This means that it require less hardware resources and swap partition could be written/readed faster?

---

### Post by justin_nita on 2007-10-01
...and also requires less time because of few operations hardware should do?

---

### Post by trippinnik on 2007-10-02
Yeah, it should be faster because it operates in RAW mode, there's no filesystem overhead to deal with.  You probably won't notice the difference though, as swap is going to be slow compared to RAM.

---

