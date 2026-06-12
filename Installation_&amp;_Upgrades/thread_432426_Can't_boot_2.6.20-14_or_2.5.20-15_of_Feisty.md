---
title: "Can't boot 2.6.20-14 or 2.5.20-15 of Feisty"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by Jengu on 2007-05-04
My upgrade to Feisty is almost complete, but I continue to have to use the older 2.6.20-13 kernel, because 2.6.20-14 and 2.6.20-15 don't boot! I've filed a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104878](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104878)

Short version of the story: I get this error when I try to boot using the 2.6.20-14 and 2.6.20-15 kernels:

ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
ata1.00: (BMDMA stat 0x64)
ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag0 cdb 0x0 data 4096 in
Buffer I/O error on device sda, logical block 0
ldm_validate_partition_table(): Disk read failed

I know that 2.6.20 featured some major a new set of ATA/IDE drivers. If that's the issue, how do I disable the new ones from running? (I've read this is possible) Any other ideas for the cause?

---

