---
title: "How do I format partition as Apple_Bootstrap for PowerPC?"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by Brian Kendig on 2012-10-18
I want to try installing Ubuntu on an Apple Macintosh iBook (Dual USB) from 2001, just to see if it can be done. :)

The iBook's CD drive is unable to read Ubuntu PowerPC 12.04 CDs that I've burned for it. It boots to a text display which then says "Can't read boot blocks", or which gives me read errors then dumps me at a yaboot prompt. I'm guessing the drive is too old to read CD-R media or else it's damaged, so I want to try booting the Ubuntu installer from a USB flash drive (8GB).

I understand that I need to format the USB flash drive partition as "Apple_Bootstrap". How do I do this? I can't find mac-fdisk in any repositories, and gnu-fdisk and parted both want me to enter a filesystem type but don't have Apple_Bootstrap in their lists of type codes.

---

