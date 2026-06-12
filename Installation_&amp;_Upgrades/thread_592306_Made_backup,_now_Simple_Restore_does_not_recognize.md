---
title: "Made backup, now Simple Restore does not recognize"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2007-10-26
OK. I backed up my home partition with sbackup, verified the backup, then installed Gutsy wiping the drive in the process.

Now I am trying to use Simple backup restore. When I point it to the folder (/media/disk/backup) I get an this error:
Error: no backup found in target directory. I am doubly sure that the backup is there.

Here is the output of the folder:
```
complexity@complexity-laptop:/media/disk/backup$ ls -l
total 27422224
-rwxrwxrwx 1 complexity root         144 2007-10-25 21:38 excludes
-rwxrwxrwx 1 complexity root 28049908684 2007-10-25 22:53 files.tgz
-rwxrwxrwx 1 complexity root     2154723 2007-10-25 21:39 flist
-rwxrwxrwx 1 complexity root      802886 2007-10-25 21:39 fprops
-rwxrwxrwx 1 complexity root       34320 2007-10-25 22:53 packages
-rwxrwxrwx 1 complexity root           4 2007-10-25 22:53 ver

```
What to do?

---

### Post by lsutiger on 2007-10-26
bump

---

