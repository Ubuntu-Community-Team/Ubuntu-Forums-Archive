---
title: "reclaim partition"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by scotch_neat on 2013-03-25
A while back I had a failed install of Ubuntu 10.04, the partition is there, I can see the mounted partition from my successful 12.04 install. I want to either empty the partition (can't access to delete from working partition) or reclaim the space into my current, working partition.

Did that make any sense?

BTW... I am not an Ubuntu adept - basic user.

Thanks very much.
Stephen

---

### Post by darkod on 2013-03-25
It would have been much better if you did that before the 12.04 install. Yes, you can delete it now but to expand your current 12.04 root partition first of all they have to be next to each other, and second resizing does involve certain degree of risk so you should make a full backup of your 12.04 before expanding it.

Open Gparted or parted in terminal and note where the partitions are. Post a screenshot if you need help and let us know which partition is which.

---

