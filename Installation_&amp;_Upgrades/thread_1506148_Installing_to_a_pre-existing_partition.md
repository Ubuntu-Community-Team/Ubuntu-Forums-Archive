---
title: "Installing to a pre-existing partition?"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by Nater43 on 2010-06-10
What I am trying to accomplish, is have 3 partitions on my hard drive. The first one being Windows 35GB. The second being 15GB Ubuntu. The remaining just being backups. I have set up partitions for this, but I have failed thus far in finding a way to install to the Ubuntu partition I have created. Should I have left that space unallocated? How would I make this work?

---

### Post by dvlchd3 on 2010-06-10
When going through the install process, select Manual when asked where you want to install Ubuntu.

Find the partition you want to install Ubuntu on, select it, then select change.
File System: EXT4
Mount Point: /
Format: [Check]

This will format the partition with EXT4, and set it as the / (root) mount point where the Ubuntu files and boot files will be installed.

---

