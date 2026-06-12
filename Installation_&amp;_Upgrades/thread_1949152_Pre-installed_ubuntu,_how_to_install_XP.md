---
title: "Pre-installed ubuntu, how to install XP"
date: 2012-03-29
forum: Installation &amp; Upgrades
---

### Post by varuagaurav on 2012-03-29
I just got myself a new Dell Vostro 1450 Laptop that came pre-installed with Ubuntu 10.10

I  have a licensed XP CD with me and have tried to boot through it to  install windows. However it always fails quoting some Hard Disk related  error. 

Not sure but I think that this may be due to filesystem mismatch (have been told so)

I don't actually need to keep Ubuntu and don't mind losing it, as long as I am able to install XP

Can somebody suggest a way to install Windows XP on my laptop please. Would really appreciate it

---

### Post by darkod on 2012-03-29
You don't mind losing it, or you WANT to overwrite it with XP? There is a huge difference.

If you like to keep ubuntu, you need to shrink the partitions to make unallocated space. If you want to overwrite it, you simply don't bother about that and install over it.

In any case, XP is ancient so the first thing you need to check is whether it will detect the hdd at all. Most new computers come with sata mode set to AHCI and XP sometimes can't detect the hdd unless you change that to IDE.

Boot with the XP cd and let it start loading the installer. Go through the first few steps until you reach the disk partitioning screen. If it can't detect the hdd it will report it.

First check if it detects the hdd, then you can think further.

---

### Post by restorator on 2012-03-29
If I remember correctly, XP would sometimes have a problem when filesystem was not windows readable. What you should do is throw the ubuntu cd in the drive and fire up your computer in live mode from the cd. (try without installing). Use gparted to delete all the partitionas and then create a new one and format it NTFS. After that XP should have no problems with the filesystem.

---

