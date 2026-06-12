---
title: "ext2 and user_xattr"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by mvelicu on 2009-12-10
Hello 

How I can add user_xattr  attribute to a ext2 partition in fstab file

An why ubuntu 9.1 server install by default ext 2 partition instead on ext3 or ext4

Regards,
Mihai

---

### Post by lemming465 on 2009-12-12
Ubuntu 9.10 uses ext4 by default, but the partition type code byte (as seen by *fdisk -lu* or the like, will still be 0x83, which displays as ext2.  ext3 and ext4 are forward (but not backward) compatible with ext2.  One crude way to tell the difference is to run *sudo tune2fs -l ...* against the partition; if the features include *has_journal* it's ext3 or later, and if it has *extent* it's ext4.  If it doesn't have user_xattr try turning that on with *sudo tune2fs -O user_xattr ...*

---

### Post by mvelicu on 2009-12-14
I tried how you said but I have this error 

mihai@userver03:~$ sudo tune2fs -O user_xattr /dev/sda1
tune2fs 1.41.9 (22-Aug-2009)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
mihai@userver03:~$ 


What should I do ?

Regards,
Mihai

---

### Post by lemming465 on 2009-12-16
What output do you get from```
sudo -i
fdisk -lu
blkid
mount
```
Knowing more about your disk structure will help understand it.

Your specific error message suggested that partition sda1 wasn't a valid ext2 style filesystem.  It could be damaged, or the ext2 partition could be somewhere else, or there might be RAID or LVM devices involved, or something.

---

