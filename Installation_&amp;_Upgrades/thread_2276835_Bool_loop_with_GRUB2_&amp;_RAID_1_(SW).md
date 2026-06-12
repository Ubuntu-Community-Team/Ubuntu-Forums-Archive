---
title: "Bool loop with GRUB2 &amp; RAID 1 (SW)"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by p-launchpad-w on 2015-05-05
This is the output of boot-repair-disk: [http://paste.ubuntu.com/10989457/](http://paste.ubuntu.com/10989457/)

My system is running Ubuntu 14.04 LTS and has two drives that are used for RAID 1 (two RAID partitions.) It is configured to boot from EFI first.

It started with a failing drive which I swapped it for a new one. The drive that failed had the EFI partition. I created a new EFI partition on the new drive and ran boot-repair-disk which did the trick and the machine booted fine.

The failing drive made the swap partitions getting lost, so I re-created them, one on each drive. After this when I rebooted, the machine just goes into a boot-loop. I ran the boot-repair-disk again, but it did not solve the issue. The output of the repair session is posted in the beginning of this post. 

I'm unsure of what I should do now, any suggestions and hint would be highly appreciated.

Regards, Peter

---

