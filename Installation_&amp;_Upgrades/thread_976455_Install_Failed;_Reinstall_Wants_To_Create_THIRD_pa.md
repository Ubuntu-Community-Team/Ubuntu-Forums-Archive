---
title: "Install Failed; Reinstall Wants To Create THIRD parttion"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by jretzer on 2008-11-09
Ubuntu newbie question: 

I tried to install the latest version on a Windows XP machine. The install failed with about 70% done. I burned a new disk and tried to reinstall. Now it wants to create a THIRD partition; there will be the XP partition, a 10 GB partition with a failed install, and a 20 GB partition for the fresh install.

Don't want that dead space, or a third partition. How do I fix this?

TIA

---

### Post by jretzer on 2008-11-13
Help, please

---

### Post by louieb on 2008-11-13
Use the manual partitioning option.

If you need help with it. I would like to see the partition table.

boot the live CD and open **applications>accessories>terminal**
and post the output of ```
sudo fdisk -l
``` lowercase L at the end

---

