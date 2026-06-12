---
title: "Raid?"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Burillo on 2008-05-01
I've got a computer with Vista and RAID on it. When i boot Kubuntu LiveCD it sees three harddrives (sda, sdb, sdc). I don't want to install i just want to tweak partition table a bit. How can i make it to see the disk as one?

The RAID disk is 3 harddrives partitioned into 3 NTFS partitions. Vista is on the first one. The reason is i'm going to install XP there on 2nd partition. I was going to fool XP into thinking it's being installed on first hard drive by marking 1st partition as Hidden NTFS, as i did before. So i booted Ubuntu LiveCD and was surprised when i saw three hard drives separately instead of one RAID drive. So any partition table editing is dangerous.

---

### Post by aroddo on 2008-05-03
try to install dmraid when running the live cd.
after that the partition editor should show the raid partition, too.

---

