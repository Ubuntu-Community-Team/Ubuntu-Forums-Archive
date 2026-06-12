---
title: "Files System?"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by hc2995 on 2006-09-05
What file system does ubuntu require? iv fromatted swap for fat 32 and root for fat 32 so if someone can tell me what each requires thanks.


PS on fat 32 i get "Incorrect file system for mount point"

---

### Post by chippy99 on 2006-09-05
Linux does not use fat32. File systems are either ext2, ext3 or reiser fs. Swap is linux swap. What are you using to format the partitions ? You can reformat them in the installation program.

---

### Post by brucevangeorge on 2006-09-05
Ubuntu uses its own filesystem. The linux ones like; ext1, ext2, ext3, XFS, jfs, reiser3, reiser4.

The default one is ext3. 

AND, Ubuntu cannot install on FAT32. That is Windows only.


You need to reformat. So take a Ubuntu CD and reinstall it. If you use the livecd it will do it when you install to your computer.

If you want to have a choice in the filesystem that Ubuntu uses... you have to use the "alternate install cd".

Do some research into the different filing systems before changing!!

---

### Post by hc2995 on 2006-09-05
ok swap = linux-swap
root = EXT3

lemme install it now thanks :D

---

