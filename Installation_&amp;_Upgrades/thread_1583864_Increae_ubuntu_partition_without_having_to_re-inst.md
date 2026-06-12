---
title: "Increae ubuntu partition without having to re-install"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by sridarshan on 2010-09-28
I am using my laptop with 10gb ubuntu partition and rest as windows partition,Is there anyway in which i can increase my ubuntu partition without having to re-install the ubuntu OS?

---

### Post by oldfred on 2010-09-28
You can.

You will have to shrink your windows partition with gparted. You have to leave 20-30% free in windows for it to keep working well. If you have the Ubuntu partition to the right (installed after win) then it may take a while to move the Ubuntu partition and do not interrupt the move.

Or you can create a new partition if you have not used all four primary partitions or have some partitions in an extended partition. Then you can move /home into the new partition. Root only needs 10-20GB.

Expanding/Resize an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Advanced resizing:
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

