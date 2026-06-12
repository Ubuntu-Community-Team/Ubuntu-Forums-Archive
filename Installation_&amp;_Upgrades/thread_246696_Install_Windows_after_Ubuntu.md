---
title: "Install Windows after Ubuntu"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by tombiz on 2006-08-29
I have installed Ubuntu as my sole OS on my desktop PC. However, I would like to add Windows XP Pro as my other OS to run some of my apps. Is it possible to install Windows XP Pro after Ubuntu has been installed? If so, do I simply resize my main partition where Ubuntu is installed and format it as NTSF and part of it as FAT32 to access my files on both platforms?

Thanks.

---

### Post by zxee on 2006-08-29
Linux in general is getting better at reading _and_ yes writing to NTFS (do a search) there are threads in this forum.
However installing win after linux is not a good thing because windows will overwrite your mbr and therefore you won't be able to boot into ubuntu until you restore grub to the mbr. You'll probably want to use the ubuntu live/install cd to do that.

---

