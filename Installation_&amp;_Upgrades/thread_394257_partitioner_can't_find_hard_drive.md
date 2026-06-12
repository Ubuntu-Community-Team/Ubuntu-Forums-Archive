---
title: "partitioner can't find hard drive"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by elsaturnino on 2007-03-26
I'm attempting to upgrade an old debian server to ubuntu 6.06 LTS server. However, when I get to the stage where I need to set my partitions, the installer can't seem to find my hard drive. It sits there indefinitely until I hit ctrl-c at which time it takes me to the partition screen but without any hard drive to partition. The strange thing is, when I do "fdisk -l" in my current debian installation, it can't find the hard drive either.  Anyone have any idea what might be happening here?

Thanks!

---

### Post by taurus on 2007-03-26
Get into the BIOS and see if the BIOS even detects your harddrive.

---

### Post by elsaturnino on 2007-03-26
> **taurus said:**
> Get into the BIOS and see if the BIOS even detects your harddrive.

I'll check that when I get back to the office but does it make sense that the BIOS wouldn't detect it yet my debian installation is usable?

---

### Post by elsaturnino on 2007-03-27
Just a bit more info so (hopefully) someone can help... While "fdisk -l" results in nothing, "fdisk -l /dev/hda" gives me the correct partitioning as it stands on my debian install. This should be recognized during my ubuntu install process, right?

---

