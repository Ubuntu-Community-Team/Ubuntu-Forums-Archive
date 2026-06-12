---
title: "Dual OS Accessing Files"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by GTar on 2005-08-04
Hi,

Just planning on a clean Windows XP and Ubuntu installation on a new PC I've built. This wont be a problem as I've done it several times before.
I was planning on having 3 seperate partitions, one for Windows XP, one for Ubuntu and another for storing documents, images, music etc.
My question is what would be the best file system to use on the 3rd storage partition?? I need to be able to quickly read and write to it from both WinXP and Ubuntu.
Any suggestions? Maybe there's an easier way to do this?

---

### Post by jasmuz on 2005-08-04
I recommend that the 3rd partition you make it a FAT32 one, thus allowing you to read and write under both OS.

---

### Post by frodon on 2005-08-04
I think you should use FAT32, it's not the best system format about performances but as long as windows will not see ext3 format and linux will not be able to  write NTFS (with a good speed) I don't think there is another good alternative, it's my opinion.

---

