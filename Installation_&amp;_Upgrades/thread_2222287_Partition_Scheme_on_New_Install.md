---
title: "Partition Scheme on New Install"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by XBMC old School on 2014-05-05
I've seen in a few instances were people have set up their partitions as follows:

/
/usr/
/var/
/tmp/
/home/
swap

Is there any real advantage to this for a regular desktop user? Is there any advantage to having them on different type of drive or fikesystem type? I have heard for performance locating /var/ on a ramdisk is good, and /home/ on an HDD is good as well. Please redline in any pointer or comments.

---

### Post by oldfred on 2014-05-06
Default install is / (root) and swap. For new users with a smaller / that is all that is needed. I only had that plus a shared NTFS data partition when I was dual booting XP.

But we often suggest adding either /home or a data partition as an additional partition. Separate /home can make reinstall easier as you can just remount it without reformatting that partition. 

But I prefer reliability. So I have all system including /home inside / on every drive. Then each drive can be booted without any other drive. And then I have separate data partitions. I find my working install on a SSD uses about 11GB out of my 25GB / (root). And then I have large data partitions for all my data on a rotating drive.

---

