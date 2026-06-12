---
title: "Lucid upgrade: wine can't see windows partition though it is mounted"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by muzincs on 2010-08-17
Rsnapshot also cannot see my external hard drive.  But I can see/edit all the files in the windows partition and the external drive.  The output of mount for those two entries is:
/dev/sdb1 on /media/Expansion Drive_ type fuseblk (rw,nousid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/windows type fuseblk (rw,nousid,nodev,allow_other,blksize=4096)

This is the fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda6 :
UUID=4b0749b1-09c9-4869-bee3-4253ef99af08	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=ae9f2067-4416-4b89-b97f-34ba8d24f7c3	/home	ext3	relatime	0	2
#Entry for /dev/sdb1 :
UUID=DC6432FD6432DA4A	/media/Expansion\040Drive_	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
#Entry for /dev/sda2 :
UUID=42007629007623D7	/media/windows	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda5 :
UUID=bdd30a46-7d55-4e2e-b495-8c7da3b0b216	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0
```

Any ideas?

---

### Post by muzincs on 2010-08-17
Does this thread belong on another forum?

---

