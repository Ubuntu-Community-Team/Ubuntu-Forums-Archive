---
title: "cannot see any other files/folders on /home partition"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by dancer_69 on 2012-05-24
Hello,
I recently install ubuntu 12.04, and I used a btrfs partition on another disk for /home.
The problem is that now all other files on this partition are hidden and I cannot have access to them. The home directory has only the subdirectory of user. 
I know that all these files/folders still exist, because I can have access on them if I boot to my other linux lmde installation.
This is the entry for /home on fstab:
```
# /home was on /dev/sdb5 during installation
UUID=c583901f-74e4-4c00-8498-129c0d7d1cf2 /home           btrfs   defaults,subvol=@home 0       2
```
I did the same before some time with ubuntu 11.04 without this problem.
How can I solve it?

---

### Post by dancer_69 on 2012-05-25
I found the solution myself.
Ubuntu create the folder @home in btrfs volume, and mounted this folder only.
I've managed to mount the root of btrfs volume on another directory on /media. So now I have access to all content.

---

