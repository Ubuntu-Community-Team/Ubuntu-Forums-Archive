---
title: "How-To: Consolidate free space on Windows Vista drive"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by JohnElway on 2010-07-12
I thought I would post this to help some people who are still having trouble consolidating the free space on their Windows Vista partitions.

Most of the information you need is here:
[http://seogadget.co.uk/how-to-resize-a-windows-vista-partition/](http://seogadget.co.uk/how-to-resize-a-windows-vista-partition/)

**HOWEVER**, the above guide might not work for everyone (didn't work for me). The problem is that there may still be some system files running in the background that prevent all of your free space from consolidating. For some reason, I didn't find many partitioning guides that mention this.

If you find at Step 11 that your shrink space is still abnormally small, what you need to do is go back and open PerfectDisk. With "Consolidate Free Space" selected in the drop down box, click the "Boot Time" button. This allows PerfectDisk to consolidate free space while your hard drive is offline. Once this is done, go back to Step 10 and everything should work from there!

---

### Post by Mark Phelps on 2010-07-13
Since this is NOT a Vista forum -- folks might not be aware that following the guide you linked to will remove their Restore Points!

That's a really high price to pay just to shrink a partition.

---

