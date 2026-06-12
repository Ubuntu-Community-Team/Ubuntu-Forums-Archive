---
title: "Clean Install Instead of Upgrade, I have separate Home partition"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by kendoori on 2010-06-04
Can someone point me to details regarding upgrading from 9.10 via clean install, while retaining settings/packages. My current setup has separate home partition, but no swap partition (I have a swap file) and also dual boot with original XP.

I might just image my machine and take my chances with in place upgrade, but want a plan B.

---

### Post by darkod on 2010-06-04
The personal settings, including settings for some packages are inside your Home folder, in your separate /home partition.

But the packages are not saved by default. There are different ways to reinstall your packages that were installed by Synaptic or apt-get, for example this:
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Otherwise, the way to clean install with separate /home is:

You start the installer and use manual partitioning. Both your / and /home partitions (since you don't have swap part) will be shown as unused, I guess to prevent wiping them by mistake.

Click on each partition, the button Change at the bottom, and select the correct filesystem (it they are ext4 select ext4 again), the correct mount point and FORMAT / but DO NOT FORMAT /home.

Formatting / will make it real clean install otherwise remains of the older OS might be there. Obviously, never format the /home partition if the intention is to keep the data.

That's it. If you had a swap part you would just select it as swap again the same way.

PS. Run 10.04 in live mode first to make sure there are no hardware issues.

---

### Post by moonport on 2010-06-04
I've tried either update manager and clean install upgrade methods.
It's true that you can keep your info save into the /home partition, but in my opinion, if you have enough time, update manager is better & safer.

---

### Post by oldfred on 2010-06-04
Another thread on the same topic. With additional comments.

[http://ubuntuforums.org/showthread.php?t=1501430](http://ubuntuforums.org/showthread.php?t=1501430)

---

