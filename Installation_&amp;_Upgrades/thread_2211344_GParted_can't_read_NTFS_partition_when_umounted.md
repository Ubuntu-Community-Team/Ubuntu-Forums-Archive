---
title: "GParted can't read NTFS partition when umounted"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by lordpuppet on 2014-03-15
Hey guys,

I wish to resize a NTFS partition, but I can only see details of the partition on Gparted when is mounted.

Whenever I umount it, I get "Unable to read the contents of this filesystem! Because of this some operations may be unabailable"

It suggests I need ntfsprogs / ntfs-3g. Which I have, but had to install ntfsprogs though (within my live usb session)

How can I get the info while ummounted?

---

### Post by sammiev on 2014-03-15
Install gparted live to a usb stick and boot from the usb stick. Always great to have a backup first of the HDD before doing anything.

---

### Post by lordpuppet on 2014-03-15
I already have Gparted on a USB live session on Mint. If I can't do it with that, could I do it with just Gparted-live?

---

### Post by sammiev on 2014-03-15
If you booted from the Live USB stick ( even if it's Mint ) you should beable to resize the NTFS partition well unmounted.

---

### Post by Mark Phelps on 2014-03-15
If the NTFS partition contains a recent Windows OS (e.g., Win7 or Win8), then do NOT use Gparted to resize that partition. Windows OS NTFS partitions don't handle resizing well, and if you force that using GParted, you risk corrupting the filesystem on that partition.

If the NTFS partition does contain a Windows OS, the better approach would be to burn a CD from the ISO file for the Minitiool Partition Wizard Boot CD -- and boot from that.  That's a Windows partitioning tool and it can shrink Windows OS partitions without problems.

---

### Post by sammiev on 2014-03-15
Hmm, never had trouble resizing Win7 with gparted and do it all the time. Guess I must be sitting on a horse shoe.

---

### Post by Morbius1 on 2014-03-15
It's not that gparted can't resize an ntfs partition and if it were anything except the partition the Windows OS lives in then go for it. But for the Windows OS partition itself it just isn't worth the risk. I mean how much greater effort is there in booting into the Windows OS and doing it there?

---

