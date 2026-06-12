---
title: "Where to put my swap partition HDD or SSD?"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by DeanoCYM on 2013-08-11
Hi all,

Just about to re-partition and was looking for some advice about whether to put the swap partition on the hard drives or the solid state drives.

The system will be hibernated over the weekend. I was mainly concerned as to whether having swap partitions on the ssd would reduce their life time?
Although fast suspend/hibernate/resume times are always nice, I'm not too concerned about speed, the main objective of this set-up is uninterrupted operation during the week. Here's the set-up:

2x 64GB SSD RAID 1
5x 500GB HDD RAID 5

Cheers!

Rhys

---

### Post by Jonor on 2013-08-13
I'd want to get an idea how much the swap gets used.
Lots of RAM capacity would swing it more to the ssds if swap barely gets used.
To check memory usage put into a terminal :
```
free
``` 
or
```
top
```

---

### Post by DeanoCYM on 2013-08-15
Hi, thanks for the help. Sadly its in bits lying around the office at the moment but there's 8GB of RAM, I've never seen it use above 6GB so I doubt that the swap is used much during normal operation but the machine is hibernated regularly.

---

