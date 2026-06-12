---
title: "&quot;No root file system&quot; even though I'm specifying it"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by kamagurka on 2006-12-10
I'm trying to replace my existing install with Ubuntu, and I can't get past the "Prepare mount points" step. Even though I'm telling it which partition to use as / and there's a ReiserFS on there, it won't let me click forward without showing me that damn "No root file system" error.

---

### Post by taurus on 2006-12-10
Are you using the LiveCD?  Try using the alternate CD to install since you have more control over the partitioning part!!!

---

### Post by Verbunk on 2006-12-12
I had this error too. The fix? Well for me it was go back to the partitioner, remove the partitions then create them. The installer will see they are new and want to format. Everything works great. You cannot just format and try to install, I tried that, no workie. The only way was to remove and recreate, in my case, the /boot, swap, and / partitions I would assign.

 -Cheers.

---

