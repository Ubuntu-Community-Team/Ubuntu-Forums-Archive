---
title: "2 &quot;empty&quot; Ubuntu partitions after installation failure"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by kallebas on 2009-12-15
I have been trying to install ubuntu and to be able to dual-boot it with windows XP. But when I was installing it I got a read-from-disc error two times in a row while I was halfway through the installation. I think I have found a CD without any defects after using the "Check disk for defects"-tool. But the problem is that I now have 2 "empty" ubuntu partitions and I do not know how to free these partitions. Is it possible to free these partitions during the ubuntu installation or use some other tool?

---

### Post by darkod on 2009-12-15
Boot with the cd and Try Ubuntu option first, open Gparted (in System-Administration) and it will allow to delete any partitions you want. If some partition has padlock (keys) symbol that means it's mounted and it can't be deleted like that. Use right-click Unmount, or for swap area Swapoff. Then you can delete it.
BE CAREFUL which partitions you delete. If you delete the wrong one you can lose data. After you do the operations in Gparted they are only scheduled, not executed immediately. You need to click the big green tick mark button to execute them.

---

### Post by audiomick on 2009-12-15
probably the best thing would be to start gparted from the live CD and remove the two "empty" partitions with that.
That will give your installer a clean slate to work with.

It would also be possible to choose the manual option for partitioning during the install and re-format them from there.

---

### Post by kallebas on 2009-12-15
Thank you for the help, everything appears to be correct now :)

---

