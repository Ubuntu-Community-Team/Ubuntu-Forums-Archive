---
title: "Strange backup problem .."
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by dgharmon on 2012-09-12
I used DD to make a backup of sda1 on sdb2, now the system boots from sdb2 and both partitions have the same UUID.

I just ran sudo tune2fs -U time /dev/sdb2, so if I'm not back in five minutes that means I've borked my system again ... System successfully booted from sda1.

---

