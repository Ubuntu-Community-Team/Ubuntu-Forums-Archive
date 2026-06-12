---
title: "Text based installer?"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by tgeof on 2006-12-23
Normally I install ubuntu via PXE, but this time I actually downloaded the install disk because bittorrent is way fast.  So I booted it up, and it threw me in a live environment with a decent install option, until I got to gparted.  I hate gparted.  It hung, as usual, and now I want my text based install back.

Anyway to do that with this install disk?

Thanks.

---

### Post by meng on 2006-12-23
Many have asked, I have always said no, I haven't seen anyone refute this. (I looked through all the boot options.) You need the Alternate CD, it's a b---h if you have limited bandwidth/download allowance.

---

### Post by kerry_s on 2006-12-23
"fdisk" or "cfdisk", maybe both should be installed. You might even want to try running "parted" in terminal.

Example:
sudo fdisk /dev/hda

sudo cfdisk /dev/hda

sudo parted

---

