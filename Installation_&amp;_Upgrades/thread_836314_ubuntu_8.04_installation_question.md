---
title: "ubuntu 8.04 installation question"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by websaytdatkom on 2008-06-21
i've already in the process of installing ubuntu 8.04 (im dual booting XP and ubuntu) i have doubt when it comes to the partitioning part. i already have partitioned a separate drive on my hard disk (using Partition Magic) Shall i go to MANUAL? when i select that partition, it says some message (i cant remember) and i wont continue..its asking me to go back to the partitioning area. when i try to edit that partition, it shows another window an there is a selection (ntfs, fat 32, etc) and there is also something about mounting,.../dos & /windows...whatever...please help..

---

### Post by wh0rd on 2008-06-21
This is a [good guide]("http://www.psychocats.net/ubuntu/partitioning") by psychocats on partitioning an XP/Ubuntu dual boot.

---

### Post by websaytdatkom on 2008-06-21
what if i choose to use manual in dealing with partition, what format is best? can i use ntfs?

---

### Post by avtolle on 2008-06-21
For your root partition ( mount point /) where Ubuntu will "live", it should be formatted ext3. The shared data partition may be formatted NFTS, if you like.

---

