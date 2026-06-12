---
title: "Expanding / Resizing a partition and filesystem"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Fed on 2007-12-30
Hi,

I've done a search but it didn't really seem like any of the threads helped me with my particular situation. Basically I've built a RAID5 array recently, made a partition, then a filesystem (xfs), everything is peachy. In the future, it is very possible that I will want to expand the array. My RAID card will allow me to expand the array very easily, so that's step 1 out of the way. Step 2 is resizing the partition, I used "parted" to make it in the first place and it seems to be that resizing it would be equally simple. So that brings me to step 3, the one I need help with - the filesystem. As far as I know, expanding the partition will not also expand the filesystem to use the new space (or will it? considering parted didn't even let me create the xfs filesystem because it's not supported by parted itself, I doubt it can modify it to use the new space either). So how would I go about resizing the filesystem / making the filesystem use the new space?

Thanks!

---

