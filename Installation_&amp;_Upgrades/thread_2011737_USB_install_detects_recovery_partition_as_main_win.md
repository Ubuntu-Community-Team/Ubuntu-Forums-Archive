---
title: "USB install detects recovery partition as main windows partition"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by andizam on 2012-06-27
Hello, I'm a bit of a newbie when it comes to Ubuntu. I plan to boot from the USB installation, and all goes well. When I choose to use my own partitions to install Ubuntu, it detects my Dell (Inspiron 15R) recovery partition as /dev/sda2, which gives me little space to install Ubuntu, and sees my ~450 GB C: drive as /dev/sda3. It only allows me to modify the /dev/sda2 drive. Any help please?

---

### Post by darkod on 2012-06-27
If you need to shrink the C: partition to make unallocated space for ubuntu, it's better to do it in windows using Disk Management. After that restart windows few times in case it wants to do any disk checks.

When you have the unallocated space you can install either with the manual partitioning or some of the auto methods, under the condition that you already don't have all 4 primary partitions used. If you already have 4 primary partitions, you will also need to delete at least one in order to be able to create the ubuntu partitions as logical partitions.

---

### Post by andizam on 2012-06-28
Ahh, thank you very much! That made sense, and it worked like a charm. Now I've other problems to post about, but this problem's solved. Thanks a ton!

---

