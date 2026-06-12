---
title: "Re-installation Help"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by age99 on 2011-05-18
Hi, I upgraded to 11.04, but the updgrade crashed, and now it has some errors with Unity crashing every time I open a terminal.  Is there any way to re-install without having to reconfigure all my programs?  I am running a dual-boot.

Thanks

---

### Post by shantanu18 on 2011-05-18
YES. Ubuntu 11.04 also provide a update option from previous version. Boot from live CD and upgrade option will appear before showing partition table. Select upgrade and it will upgrade your system applications will be ok. But which application does not support 11.04 maybe removed. Backup your data from before upgrade. If this upgrade crash then try it again. Careful about disk space in filesystem. Good luck!

---

### Post by age99 on 2011-05-18
Thanks, I'll download a live CD.  But with 11.04 already poorly installed, how will it upgrade?

---

### Post by Hedgehog1 on 2011-05-18
**When you boot from the 11.04 LiveCD/LiveUSB:**

You may have an upgrade path offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

**If this is not offered**, if you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

