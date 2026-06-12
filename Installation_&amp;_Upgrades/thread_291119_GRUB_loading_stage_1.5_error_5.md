---
title: "GRUB loading stage 1.5 error 5"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by gmcm1979 on 2006-11-02
i have tried to copy my old hdd to my new one using ghost4linux but it failed to work, when i now log on to ubuntu ut gives the error GRUB loading stage 1.5 error 5 can anyone help?

---

### Post by lha on 2006-11-02
> **gmcm1979 said:**
> i have tried to copy my old hdd to my new one using ghost4linux but it failed to work, when i now log on to ubuntu ut gives the error GRUB loading stage 1.5 error 5 can anyone help?
Your new hard drive is bigger than your old one, isn't it?

A quick googling gave me the page ([http://www.feyrer.de/g4u/]("http://www.feyrer.de/g4u/")) telling
"5.1 Supported filesystems

      One of the questions arising a lot is "what filesystems does g4u support". The answer is: "all of them". g4u reads the disk bit by bit, starting from byte #0 to the end. It includes any MBR, boot record, partition table and the partitions themselves without further investigating the structure of the data stored in these partitions."

This gives me the reason to believe that your problem lies in incorrect partition table because Grub error 5 means
"Partition table invalid or corrupt
    This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign." 
As your hd's are of different size, their partition tables should differ, too. But, your new hd has the partition table of old hd and Grub sees this and informs you of this problem. So you have to fix your partition table or find an alternative way to migrating to your new hd. I'd recommend the latter. I used the instructions from [Hard Disk Upgrade Mini How-To]("http://www.tldp.org/HOWTO/Hard-Disk-Upgrade/index.html") when I upgraded my hd.

---

### Post by blabla on 2006-11-02
iha's suggestion is good, simply copy info across. another possibility, however, would be to use partimage.

---

