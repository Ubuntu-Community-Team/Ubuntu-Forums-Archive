---
title: "Uninstalling ubuntu 9.10 if installed &quot;side by side&quot;"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by jakecosby7 on 2010-02-11
I've gotten rid of the GRUB bootloader and restored the default windows bootloader , and i have also deleted all other partitions that windows was not installed on but only problem is that when i first installed ubuntu 9.10 i chose to install it side by side instead of on a separate partition so now im convinced i still have some ubuntu remains on my pc. any idea on how to remove it?

because my current partition that windows runs on still shows 80gb of 136gb is free but before i installed ubuntu 136 gb was free  so im sure i still have some ubuntu left. how do i fully get rid of ubuntu if i chose to install ubuntu "side by side" instead of on a separate partition?
I am running windows vista sp1 on hp dv4

---

### Post by bcbc on 2010-02-11
If you deleted the partitions that Ubuntu was installed on, this would have left the space unallocated and your Windows is still looking at the resized partition created when you installed ubuntu. You'll need to allocate the unused space by creating and formatting a new partition so that it's available to Windows again.

---

