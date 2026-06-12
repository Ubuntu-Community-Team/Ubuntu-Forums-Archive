---
title: "Deleting Ubuntu patitions"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by alextsl on 2011-05-14
I had Ubuntu 11.04 for about 2 weeks now and I want to install Windows 7. The problem is that I can not delete the Ubuntu partitions in the Windows setup. I don't want to dual boot, I just want to delete them. Is there any way I can do this without affecting my other 2 partitions, which are NTFS?
Please note that I am not very good with Ubuntu, so I would need a step-by-step guide.

---

### Post by wilee-nilee on 2011-05-14
> **alextsl said:**
> I had Ubuntu 11.04 for about 2 weeks now and I want to install Windows 7. The problem is that I can not delete the Ubuntu partitions in the Windows setup. I don't want to dual boot, I just want to delete them. Is there any way I can do this without affecting my other 2 partitions, which are NTFS?
Please note that I am not very good with Ubuntu, so I would need a step-by-step guide.

Use a Ubuntu disc to remove the Ubuntu with gparted and put a ntfs partition in its place with gparted. Right click the swap then swap-off to do this removal.

Then, this is important right click the new ntfs then flags click boot then run it like when you removed the partitions. Boot the W7 disc and install to that partition

---

