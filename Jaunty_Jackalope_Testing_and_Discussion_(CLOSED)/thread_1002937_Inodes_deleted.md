---
title: "Inodes deleted ?"
date: 2008-12-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-12-05
On my latest boot of Jaunty I noticed the following messages:
```
[   15.498059] EXT3-fs: sda7: orphan cleanup on readonly fs
[   15.498110] ext3_orphan_cleanup: deleting unreferenced inode 2679874
[   15.498166] ext3_orphan_cleanup: deleting unreferenced inode 2679872
[   15.521840] ext3_orphan_cleanup: deleting unreferenced inode 2679870
[   15.521856] ext3_orphan_cleanup: deleting unreferenced inode 2679869
[   15.533748] ext3_orphan_cleanup: deleting unreferenced inode 2679863
[   15.543553] ext3_orphan_cleanup: deleting unreferenced inode 2678931
[   15.543727] EXT3-fs: sda7: 6 orphan inodes deleted

```
Taken from dmesg. As far as I'm aware my last shutdown of Jaunty was fine. What are these inodes ? Are they a warning that I may have future problems ?

---

