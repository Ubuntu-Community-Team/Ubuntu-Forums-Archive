---
title: "Loosing Data With Gutsy Install"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by mgaskell on 2007-10-27
I just hosed my ability to boot into my old Windows system by moving the NTFS partition in order to get ready for Gutsy. I used Gparted. I tried Super Grub Disk to try and recover a MBR but noting worked. I now have one NTFS partition (/dev/hda2). The data can be found when I boot using the Gutsy install CD  but Windows no longer boots. If I just let Gutsy install from the CD will the partition scheme destroy the data in the NTFS partition or will it create an ext3 partition in an unallocated part of the drive?

Thanks

---

### Post by Pumalite on 2007-10-27
What do you want to do about your Windows. It doesn't seem to be working. You are better off installing with Alternate CD and pointing to the right partition.

---

### Post by mgaskell on 2007-10-27
I would ideally like to set up a dual boot system using my existing Windows install. I think I buggared that up so I want to recover the data and reinstall Windows.

---

### Post by Pumalite on 2007-10-28
You can recover data with your Live CD or Knoppix. Install windows first, then Ubuntu.

---

