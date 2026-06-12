---
title: "Mount Point"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by selchi on 2008-04-13
I am installing Ubuntu for the first time; and I dont know what I should select for Mount Point.

Right before I started installation process of Ubuntu, I made a new partition with Magic Partition and give it space of 20GB.

Under the PREPARE PARTITION windows, here are the listings for the new partition that I made with 20 GB.

DEVICES: /dev/sdb5 TYPE: ext2 MOUNT POINT: /windows FORMAT: check SIZE: 21476 MB USED: 68 MB

Ok; after that point, it is asking me to select the right MOUNT POINT - What should I select?

If my above selectins are wrong, please advise me and tell me what selections should I make for TYPE and MOUNT POINT. 

Thank you.

---

### Post by ibutho on 2008-04-13
You need to create at least 3 partitions for use with Linux. One should have a mount point of / which contains most of the systems files, packages etc. The other should be /home which is for all user directories. Both of these partitions can use the ext3 filesystem type. A third one is swap (usually 256MB to 1GB), which is used like virtual memory.

---

