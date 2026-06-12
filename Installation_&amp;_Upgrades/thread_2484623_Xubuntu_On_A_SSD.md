---
title: "Xubuntu On A SSD"
date: 2023-03-04
forum: Installation &amp; Upgrades
---

### Post by davereyn on 2023-03-04
Looking at replacing my current computer, the one I'm looking at has a SSD, [COLOR=#000000][FONT=lato]1TB NVMe M.2 SSD (2400MB/R, 1950MB/W), I've not installed on a ssd before so anything different than a normal hard drive? Any possible problems to look out for? Do I partition the same? Is there a guide available?[/FONT][/COLOR]

---

### Post by ubfan1 on 2023-03-04
Two things to be aware of: 1) alignment (sector 2048 of 512 B sectors is 1M) and 2)overprovisioning (saving some unused sectors to replace worn out ones).  The alignment is pretty automatic these days, most default starts at 2048 instead of the old 63.  The overprovisioning may be harder to determine.  Some claim drives save the necessary sectors themselves and do not even offer them for your use.  Maybe, maybe depends upon manufacturer.

---

### Post by oldfred on 2023-03-04
Backup may be more important. 

HDD's write to unused space, so old files can be recovered in some cases.
SSD regularly run trim, which speeds up writes as then space does not have to be erased before write. And then they manage where data is written to reduce wear.

---

