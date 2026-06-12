---
title: "No Root File System"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by s3mperfitillidie on 2010-02-06
[IMG]http://i49.tinypic.com/64o3ea.png[/IMG]

Trying to install from netbootin...gives me that error, this is so frustrating.

---

### Post by presence1960 on 2010-02-06
You are using manual partitioning correct? You must highlight the Ubuntu partition, click change and select in the drop down boxes: Use as -> select filesystem (ext4 or ext3) Tick the format box and on mount point use the drop down box to select /

If you have a swap partition on use as select linux-swap. If you have a separate /home partition select filesystem in use as, if you have data on it already **_DO NOT tick the format box_** and on mount point select /home. Proceed with the install.

---

### Post by s3mperfitillidie on 2010-02-09
> **presence1960 said:**
> You are using manual partitioning correct? You must highlight the Ubuntu partition, click change and select in the drop down boxes: Use as -> select filesystem (ext4 or ext3) Tick the format box and on mount point use the drop down box to select /

If you have a swap partition on use as select linux-swap. If you have a separate /home partition select filesystem in use as, if you have data on it already **_DO NOT tick the format box_** and on mount point select /home. Proceed with the install.


What are you talking about? The options are blocked, and it doesn't show my drives/partitions 

[IMG]http://i45.tinypic.com/a4pki9.png[/IMG]

---

### Post by buttie on 2010-02-10
It's known issue in Karmic (both x86 and x64), for some reason installer recognize disks as RAID array even it there ever wasn't any.
Try this solution: [http://ubuntuforums.org/showthread.php?t=1380077](http://ubuntuforums.org/showthread.php?t=1380077)
Read more here: [http://ubuntuforums.org/showthread.php?t=1324025](http://ubuntuforums.org/showthread.php?t=1324025)

---

### Post by darkod on 2010-02-10
> **buttie said:**
> It's known issue in Karmic (both x86 and x64), for some reason installer recognize disks as RAID array even it there ever wasn't any.
Try this solution: [http://ubuntuforums.org/showthread.php?t=1380077](http://ubuntuforums.org/showthread.php?t=1380077)
Read more here: [http://ubuntuforums.org/showthread.php?t=1324025](http://ubuntuforums.org/showthread.php?t=1324025)

Unless you are actually using RAID, in which case don't remove it or you'll mess up your array.
There is different procedure to install ubuntu on RAID.

---

