---
title: "Decision on filesystem for large data partition"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by matthias_k on 2005-10-07
Hi,

I am going to wipe Debian on October 13th and install Breezy on my desktop PC. Now, since I also intend to convert a large data partition (> 200GB) from FAT32 to some linux filesystem (I don't really use Windows anymore), I'd like to hear your opinions about which one is best suited for large data partitions.

All my other Linux partitions have been running ext3 so far. But is this also a good choice for a data storage? Do I need journalling there at all? Which filesystem would you choose for a data partition?

Thanks in advance.
- Matthias

PS: Is reiser4 already in the stable 2.6.x kernel series?

---

### Post by Quartus on 2005-10-07
I have 120GB, 200GB and 250GB disks with ResierFS and no problems encountered so far. Journalling is a good choice since it speeds it up on such large disks.

---

