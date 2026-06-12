---
title: "Can't see hard disks"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by supulton on 2008-10-22
I know you hear this a lot here, but I'm new to all of this.

The problem is when I'm about to install from the live-CD, my partitions aren't detected in the partition editor. I've got a 20.5 GB NTSF Windows XP installation, and a 142.4 GB ext3 partition that I formatted with gparted with all of my data on it.

When I boot with the live-CD, I can see both of my drives under Computer, and can explore them and edit the files, but when I start the partition editor (either Ubuntu's or a separate gparted disc) it shows up as ~160 GB of unallocated space.

Any ideas as to why it doesn't show anything? Thanks!

---

### Post by supulton on 2008-10-24
I searched around a bit and stumbled on this thread--

[http://ubuntuforums.org/showthread.php?t=880687]("http://ubuntuforums.org/showthread.php?t=880687")

testdisk helped me solve my problem. I guess my partition table had been corrupted. If anybody has the same problem there is the link.:)

---

