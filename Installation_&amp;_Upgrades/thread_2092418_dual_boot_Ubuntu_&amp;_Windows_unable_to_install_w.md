---
title: "dual boot Ubuntu &amp; Windows: unable to install windows because of GPT partition style!"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by giuliotoma on 2012-12-07
About 2 months ago I installed Ubuntu on my laptop. Now i was trying to install both Ubuntu and Windows but when i try to install Windows it says: Windows cannot be installed in this partition as it is GPT partition style.
I have tried so many things and i think i have messed it up even more...right now i have no idea what to do anyway nor where to start from! Any idea??
Thank you in advance!

---

### Post by oldfred on 2012-12-07
Welcome to the forums.

That is correct. Windows will only boot from gpt partitioned drives if booting with UEFI. Is you system UEFI or just BIOS? Only new computers have UEFI.

There is a program that may convert from gpt to MBR(msdos). It may depend on spacing and number of partitions.

Post this:
       sudo parted /dev/sda unit s print

---

