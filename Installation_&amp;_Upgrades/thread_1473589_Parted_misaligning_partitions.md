---
title: "Parted misaligning partitions?"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by movieman on 2010-05-05
So I got my new 4k sector drive, ran parted using units of kib and created the partitions on 4k boundaries to ensure they're properly aligned. Before I copied the files over I switched to sector units and printed out the partition table, and every partition other than the first was offset by one sector from a 4k boundary, even though the kib printout claimed they were aligned.

Is parted ignoring me and misaligning the partitions or does it display sectors starting at one rather than zero? As I understand it the disk starts at sector 0 so I want the partitions to start at a multiple of 8 rather than multiple of 8 plus one. Also, the first partition did start at sector 2048 as expected when I told parted to start it at 1024k.

---

### Post by srs5694 on 2010-05-05
Parted can be tricky in this respect, and details vary from one version to another. You may want to read [this article I wrote,](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) although it doesn't go into every quirk of Parted. Basically, you're best off using the very latest version (compile it from source if necessary) and switching to sector units from the start. Personally, I think fdisk (or gdisk for GPT disks) is better for this purpose at the moment. If you use fdisk or gdisk, though, you'll need to use mkfs to create filesystems on your partitions.

---

### Post by movieman on 2010-05-05
Thanks, if I'd read that article before I started I'd have used sectors instead of kibs :). Those benchmarks are amazing, I wouldn't have expected even small files to be that much slower due to unaligned writes.

I didn't use fdisk because I wanted to create GPT partitions, I didn't realise that gdisk handles them.

---

### Post by srs5694 on 2010-05-05
I was flabbergasted when I got those results, too. I mean, up to *25x degradation*?!? It's amazing how much the different filesystems are affected, too. I was *very careful* when I aligned my final partitions on that test drive! (FWIW, it's now part of my MythTV system and I have no complaints about the drive's performance in this role.)

---

