---
title: "Windows 8.1 partition mounting problems"
date: 2013-12-25
forum: Installation &amp; Upgrades
---

### Post by adityashah30 on 2013-12-25
Hi guys,
I recently installed windows 8.1 along with ubuntu 12.04.3 lts. I do know about the fast boot in windows and subsequent mounting issues in ubuntu, so i disabled the fast boot in windows and turned off hibernation there. I have an entry for that partition in my fstab file. The problem is that even now, while booting, the windows partition is unable to mount to boot, and i have to skip it mounting there. Although, once i have booted and logged into ubuntu, i can mount the partition simply by clikcing it through nautilus. Any idea as to how can i avoid this problem and mount the partition at boot itself?

Thanks

---

### Post by fantab on 2013-12-26
Is there a SSD in the picture?
From Terminal run:
```
sudo blkid
```
The output will show the UUID of your partitions. Now compare the UUID of the windows partition from the above output with the UUID listed in the /etc/fstab against the said partition.
If they don't match then replace the UUID in /etc/fstab with the one from the output.

If the problem persists, then download and install [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), 'create a Bootinfo Summary' and post the LINK it creates here.

---

### Post by adityashah30 on 2013-12-26
Thanks a lot! I forgot that UUID would change. This worked.

---

