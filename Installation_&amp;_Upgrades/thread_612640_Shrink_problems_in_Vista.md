---
title: "Shrink problems in Vista"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by yosibeck on 2007-11-14
I have aToshiba A200 laptop with two hard disks of 100GB each.
Vista Home Premium is pre-installed.
In Explorer, both disks show 35 GB use and 65 GB free.
I want to install Ubuntu 7.10 after falling in love with it on the Live CD....
When trying to shrink the partition on the hard disk that boots Vista, it tells me I can only shrink 7 GB (!), even though 65 GB should be free.
It also anounces that "size of available shrink space could be restricted if snapshots or pagefiles are enabled on the volume".
I see that indeed in Vista's disk management window the Vista boot volume is listed with: System, Boot, Pagefiles, Crash Dump, Active, Primary Partition.
If I try to shrink the partition on the second (slave) disk, I can shrink almost the whole 65% free space, as it should be.
I have two questions that I would be gald if someone can assist me with:
1. Is it possible to install Ubuntu on the slave disk. Will this pose any problems/dangers with GRUB allowing dual boot of Vista and Ubuntu, when both boot from a different disk. Do I have to change anything concerning which disk is master, slave etc. (My greatest fear with this installation is that something will go wrong when trying to reboot after installation...)
2. Is there anything that can be done to make it possible to shrink the first (Vista) disk. I don't quite understand what a page file is and how critical it is to Vista's operation and if it can be disabled. Of course if I can install Ubuntu on the slave disk, this is less important, but I'd still like to know.

---

### Post by forestpixie on 2007-11-14
1 - when I first installed ubuntu I installed it to a slave disc without any problems whatsoever, it wasn't running vista but I can't see why that would matter.

2 - a page file is the windows virtual memory, again I'm not sure about vista - but when I did the original shrink I turned off the page file, it depends on how much on how much physical memory you've got as to how vista will perform. As long as you don't shrink it enormously I'd assume you'll be able to turn it on again.

I personally would go for the install to the slave disc.

Have a wait - someone else will come along with their tuppence worth I'm sure

Good luck

---

