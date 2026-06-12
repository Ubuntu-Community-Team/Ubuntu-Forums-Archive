---
title: "Installation on a HDD with Windows"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by bound4h on 2007-05-27
I have Windows XP on a 120GB harddrive with two partitions.

What is the easiest way to install Linux on the second (empty) partition?  It has about 40% of the memory.  All is NFTS as of now.

THanks.

---

### Post by merlinus on 2007-05-27
Download the desktop install disk image from ubuntu.com.  Burn it as a disk image, not a data disk, on a cd.

Then boot with it, click Run/Install, and when it is up-and-running, click the Install icon.

After answering a few questions, you will get to a partitioning menu.  Select your unused (second) ntfs partition, pick ext3 as the format, and things should go automatically from there.

It will set up grub, a bootloader which will allow you to choose whether to run ubuntu or windows.

Good luck!

-merlin

---

