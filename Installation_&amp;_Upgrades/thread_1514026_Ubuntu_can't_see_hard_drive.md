---
title: "Ubuntu can't see hard drive"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by harrystrent on 2010-06-20
I was trying to install Ubuntu 9.10 on an older Pentium 4 machine with Windows XP Pro already installed. I've tried this with Wubi and the usual way as well. I get the same error message: No root file system defined. Please correct this with the partitioner." When I tried to install the normal way, after having created a 28 GB unallocated space on the drive with Gparted, the partitioner couldn't see the drive, not the Windows partition, not the 28 gb of unallocated space, nothing. When I hit the "Next" button I got the aforementioned error message. Gparted, however, sees two partitions on the drive: an NTFS partition and the 28 gb of unallocated space, where I had intended to install Ubuntu. I get this same problem when I try to install 10.04.

---

### Post by darkod on 2010-06-20
If the disk was ever used in raid, it has metadata remains. Even formatting doesn't remove that.

Since 9.10, if the ubuntu installer detects metadata, it ignored the disk in a way.

From live mode, in terminal run:

sudo dmraid -r -E /dev/sda (use the correct disk name if not /dev/sda)

After you remove the meta data, the installer should work fine.

Obviously, if really using raid don't do the above, it will destroy your array. You need to install another way then.

Doing a proper full install is much better than wubi, and recommended.

---

### Post by harrystrent on 2010-06-20
Actually, I think it was used in RAID at one point. Thanks. When I get the chance I'll try your advice.

---

### Post by harrystrent on 2010-06-20
Indeed, that was the ticket! Thanks again.

---

