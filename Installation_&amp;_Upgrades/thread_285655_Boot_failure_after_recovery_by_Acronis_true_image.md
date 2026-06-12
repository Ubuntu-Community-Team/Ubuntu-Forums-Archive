---
title: "Boot failure after recovery by Acronis true image"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by chrysler on 2006-10-27
My HP nx6120 notebook installed:
hda1 Microsoft Windows XP
hda2 linux swap
hda3 ubuntu 6.06.1
hda4 fat32
All above partitions are primary.

GRUB was installed into hda3.
mbr was installed spfdisk(boot manager) [http://spfdisk.sourceforge.net/](http://spfdisk.sourceforge.net/)

First, I backup hda3 by Acronis true image 9.
Then, I restore it back.
Now, I cannot use spfdisk to boot hda3 now.
It seems like that Acronis true image cannot backup grub loader in hda3.
How can I do to solve this problem.
Thank you.

---

