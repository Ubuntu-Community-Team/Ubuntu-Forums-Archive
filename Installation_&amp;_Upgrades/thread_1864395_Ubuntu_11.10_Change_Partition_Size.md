---
title: "Ubuntu 11.10 Change Partition Size"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by ostrowlaw on 2011-10-18
Hi,

I installed Ubuntu 11.10 with the default settings.  Everything is working fine, but the partition is way too small and I want to get rid of the old partitions.  I downloaded gparted and ran it from a CD.  For some reason, it won't let me resize the partition.  I started it as sudo from a terminal.  I then tried to resize the partition from the liveCD, same result.  The partition does not allow resizing.

I know I'm missing something.

Thanks.

---

### Post by hyper2hottie on 2011-10-18
Is the partition mounted?  Make sure the partition you want to resize is not mounted.

---

### Post by youngunix on 2011-10-18
use **Disk Utility** it's a lot simpler and easier than Gparted.

pay a close attention to the partitions you are going to delete or format or else you'll wipe it clean and lose everything.

---

### Post by oldfred on 2011-10-19
As hyper2hottie says check mounted partitions.

Often liveCDs mount the swap partition to speed up things. But if in the Extended then it locks the entire extended partition. In gparted, click on swap and right click swap off.

---

