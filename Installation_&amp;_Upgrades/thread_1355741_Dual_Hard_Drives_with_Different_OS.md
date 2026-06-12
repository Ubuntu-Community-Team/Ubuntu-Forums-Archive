---
title: "Dual Hard Drives with Different OS?"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by Black Razor on 2009-12-15
Hi, I was wondering if anyone could help me figure out how to add a second hard drive to my Linux box and install windows to it and still use GRUB.  I've tried this before, unsuccessfully. I know I had to jumper pins set correctly, but the disk wasn't automounting in Linux.  

To be exact, what I am trying to accomplish here is to use GRUB, and have Windows 7 on one disk and Linux on the other.  Linux is the master.

Anyone help me, please?  I need to get this set up to get my music software back up and running.  Unfortunately, I need windows for my music station.  Any help would be very appreciated.

---

### Post by darkod on 2009-12-15
Install the new drive. Make that drive first in boot order in BIOS. This is very important step because windows will put its bootloader on the first choice drive. Install windows.
Switch your ubuntu drive to first in boot order. Grub should still be there intact. After booting ubuntu you'll have tp update grub to realize windows is here.
As for automounting the ntfs windows drive or just a partition, that's different task. It's easy to do it. I don't remember if the package was called ntfs-conf. Just google for automounting ntfs, loads of articles.

---

