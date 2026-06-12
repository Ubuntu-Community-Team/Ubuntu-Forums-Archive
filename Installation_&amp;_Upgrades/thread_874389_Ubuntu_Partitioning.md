---
title: "Ubuntu Partitioning?"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by spinverted on 2008-07-29
Just made the complete switch over the Ubuntu.  I've partitioned the system as follows:
4096 Mb Swap, 20,000 Mb /, and 475,000 Mb /Home   (500 Gb HD)
In Windows I had my system partition and then 4 100 Gb partitions for the sake of easy defragging.  Should I be doing something similiar in Ubuntu?
If I split up the 475,000 Mb, should it be into multiple /home partitions?
Please explain

---

### Post by Sef on 2008-07-30
> If I split up the 475,000 Mb, should it be into multiple /home partitions?

No, keep it as one partition.

> In Windows I had my system partition and then 4 100 Gb partitions for the sake of easy defragging. Should I be doing something similiar in Ubuntu?

Ext3 defragging is automatically done upon boot up every 25 or 30 times.

> 4096 Mb Swap, 20,000 Mb /, and 475,000 Mb /Home (500 Gb HD)

Swap doesn't need  to be bigger than 1 GB, root should be 8 - 10 GB, and the can be home.

---

