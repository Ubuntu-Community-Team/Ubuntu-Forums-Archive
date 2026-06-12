---
title: "Partition issue with Feisty install"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by trents on 2007-04-21
When trying to do a clean install of Feisty with Windows and Edgy already on the hard disk, I'm having a problem when I come to the Feisty partioner. It doesn't like my existing Ubuntu partitions. They are currently:

/dev/sda3 ext3 of about 27 gb and /dev/sda4 swap of 781 mb. Feisty partioner says I need a root partition of at least 250 mb and I need to specify a mount point. The box next to ext3 is checked but it won't let me check the box by the swap partition. Do I need another partition? The current setup was fine when upgrading from Dapper to Edgy. Why isn't it working with Feisty? I thopught ext3 was the root partition.

Steve

---

### Post by spin2cool on 2007-04-21
They slightly changed the way the installer works.  Click on the partition you want (i think there's an edit button by each?)  and there will be some options, including one that lets you set the mount point.

---

