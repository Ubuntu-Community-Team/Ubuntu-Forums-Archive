---
title: "Strange Extra Partition"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by Oven Glove on 2010-06-17
I installed ubuntu studio 9.10 in dual boot with XP a while ago but decided recently that I wanted to erase the linux partition and reinstall with standard 10.04. However, I opened Gparted from the live CD to find a strange extra partition within the ubuntu one. (check attachment)
Gparted says it's format is 'unknown' and I'm not sure what it is.

Could you please tell me if you know what it's for, whether it's important and if I can safely delete it in my reinstall.

Thanks in Advance,
Owen

---

### Post by darkod on 2010-06-17
Do you know if you had a swap partition? It might be corrupted so it's reported as unknown.

It doesn't look like it's used by windows anyway, and since you plan to delete Studio I guess it's safe to delete the partition.

Don't forget that after deleting the root and swap partitions (if that was swap) you will need to also delete the extended partition itself.

Or you can just start the 10.04 installer and use Manual Partitioning and tell it to use /dev/sda5 for / and /dev/sda6 for swap. You do that by clicking on a partition and then the Change button at bottom. Then you just select filesystem and mount point, and tick the format box if you want to format.
Swap can't be formatted so the option will be greyed out. Also it doesn't have specific filesystem, it's just used as swap area.

---

### Post by Oven Glove on 2010-06-17
Ok, thanks very much.
___________________

Owen

---

