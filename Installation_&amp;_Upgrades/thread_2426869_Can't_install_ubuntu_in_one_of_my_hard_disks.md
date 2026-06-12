---
title: "Can't install ubuntu in one of my hard disks"
date: 2019-09-14
forum: Installation &amp; Upgrades
---

### Post by juanpyv on 2019-09-14
I'm trying to install ubuntu 18.04.3 LTS in a SSD where i have windows too, but when i am in the partition wizard on the ubuntu installation I can't see the SSD were i have Windows, I just see the HDD, both disks are NTFS. Do you have any suggestions or possible solutions?

---

### Post by TheFu on 2019-09-14
Linux won't install to used space or onto NTFS.  You need to free at least 10-25G of storage on the disk and shrink partitions to leave that space empty before attempting to install.

There are all sorts of rules for how many partitions, what sort of partitions depending on the specific release of Windows, the specific release of Linux and whether UEFI or legacy booting is being used by the existing OSes.

---

### Post by yancek on 2019-09-15
You neglected to indicate which release of windows you are using.  If it is 8 or 10, it is most likely hibernated and no Linux system will mount a hibernated partition so turn off hibernation if it is on.

---

