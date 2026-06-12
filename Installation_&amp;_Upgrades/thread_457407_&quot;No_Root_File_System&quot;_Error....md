---
title: "&quot;No Root File System&quot; Error..."
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by dcghost on 2007-05-28
I am trying ti install uBuntu on my server (which already has windows) but everytime I go through the install process it tells me I have no root file system. I have already made the ext3 partition and swap, I am stumped.

---

### Post by rsambuca on 2007-05-28
Are you installing from the ubuntu liveCD?  If so, you will have to let the ubuntu installer re-format the partition that you have already made.  It is a known bug that the ubiquity installer program on the liveCD often doesn't recognize pre-existing partitions.  So just let it format the partition and you should be good to go.

---

