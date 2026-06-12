---
title: "Windows Partition Missing from grub"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by stuart221 on 2010-01-30
I was defraging windows xp and the power want off now I can only boot into ubuntu from Grub.

---

### Post by dbowlin17 on 2010-01-30
I am having an issue where grub can only boot into ubuntu and windows 7, and not xp for me. if i find something that works for me, i will let you know, just hope that you didn't corrupt your os...

---

### Post by oldfred on 2010-01-31
Windows will set some flags on partitions that need repairs, if that flag is present Ubuntu will not mount it.

You could try - change sda1 to your windows partition:
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk".

If that does not work you may have to use the windows CD and run repairs.

[http://ubuntuforums.org/showthread.php?t=1392524&page=2](http://ubuntuforums.org/showthread.php?t=1392524&page=2)
See this thread on Vista (should work for repairs but not install of MBR) repairs & post #38
[http://ubuntuforums.org/showthread.php?t=1348768](http://ubuntuforums.org/showthread.php?t=1348768)

---

### Post by stuart221 on 2010-02-02
s

---

