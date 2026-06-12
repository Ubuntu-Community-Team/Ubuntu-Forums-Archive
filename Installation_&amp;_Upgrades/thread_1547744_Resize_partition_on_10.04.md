---
title: "Resize partition on 10.04"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by Daniel_sk on 2010-08-07
So I installed Wubi with Ubuntu 10.04 and chose the standard partition size (8GB?) and now I am running out of disc space. How do I resize this partition?

This guide didn't help:
[https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")
The download link doesn't work and LVPM doesn't support 10.04.

Any other options or do I need to re-install the whole Wubi?

Thank you.

---

### Post by bcbc on 2010-08-07
> **Daniel_sk said:**
> So I installed Wubi with Ubuntu 10.04 and chose the standard partition size (8GB?) and now I am running out of disc space. How do I resize this partition?

This guide didn't help:
[https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")
The download link doesn't work and LVPM doesn't support 10.04.

Any other options or do I need to re-install the whole Wubi?

Thank you.

You could partition your drive and install ubuntu direct to that. It's possible to migrate your existing wubi install to the new partition ([http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354))

Or, you could use the instructions in the wubi guide to create a separate /home virtual disk - that will buy you more space as well. EDIT: I see you said that this doesn't work. Can you describe what happens when you try it? Maybe it's a usage problem as the code looks alright to me.

Or you could move some data to the /host directory (your windows partition that wubi is installed on).  

You might want to backup the root.disk before you attempt these things (it will backup the wubi install for you - if you need to you can just replace root.disk with the backed-up one). If you create a separate /home you'll also need to backup the home.disk in the future.

---

### Post by Daniel_sk on 2010-08-07
It worked this time, I don't know what I was doing wrong - the script did the job. Thanks.

---

