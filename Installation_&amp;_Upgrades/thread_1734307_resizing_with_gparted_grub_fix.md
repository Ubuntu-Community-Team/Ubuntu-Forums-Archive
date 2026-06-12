---
title: "resizing with gparted: grub fix"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by henged on 2011-04-20
hello,
quick question about using gparted to resize a ntfs data partition on the extended volume: 
using onboard windows disk management i have made 75gb unallocated to add to the aforementioned ntfs data partition. 
but, after resizing extended partition, will i need to fix grub even though i will be adding the unallocated space to a storage partition and not the ubuntu boot partition?
hope that makes sense, my noob status is pretty obvious.....

---

### Post by oldfred on 2011-04-21
Be careful using windows disk management. It does not see the Linux partitions and can rewrite partition table incorrectly. It is best to only use the windows management to shrink the windows partition and then use gparted for everything else.

---

### Post by wilee-nilee on 2011-04-21
> **oldfred said:**
> Be careful using windows disk management. It does not see the Linux partitions and can rewrite partition table incorrectly. It is best to only use the windows management to shrink the windows partition and then use gparted for everything else.

That is for sure, I built a ntfs with W7 inside my extended which had 3 linux distro's, I lost the one at the beginning, went unallocated. I had an image of it no big deal for me though.

---

### Post by henged on 2011-04-21
yep, understood. i only used windows to shrink the size of the windows partition, mainly so i didn't have to fix the windows 7 boot etc. But thanks for the info.
My main problem now is that the unallocated portion of the disc is to the left of the extended partition in the gparted gui, so as i said above i'm wondering wether resizing the extended partition (but not the actual ubuntu boot partition) will screw up grub???

---

### Post by dino99 on 2011-04-21
i dont have winblows for ages now but it likes to be on the first partition.
Resizing/moving/tweaking partitions changed their previous uuid. As grub boot with these uuid, that means you need to rebuilt its menu.

- sudo blkid  let you know them
- sudo grub-mkconfig
-sudo update-grub

---

