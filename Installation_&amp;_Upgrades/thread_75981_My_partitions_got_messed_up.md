---
title: "My partitions got messed up"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by twoseids on 2005-10-14
Before I installed Breezy, I had /dev/hda6 for my root and /dev/hda8 for my /home directory. When going through the installation process, I told it to delete and then format /dev/hda6 only. Now, however, I don't seem to have a home. Awww.... Anyway, here's what my /etc/fstab looks like:

```
# /etc/fstab: static file system information. 
# 
# <file system> <mount point> <type> <options> <dump> <pass> 
proc /proc proc defaults 0 0 
/dev/hda8 / reiserfs notail 0 1 
/dev/hda1 /media/hda1 vfat defaults 0 0 
/dev/hda2 /media/hda2 ntfs defaults 0 0 
/dev/hda5 /media/hda5 ext3 defaults 0 2 
/dev/hda7 /media/hda8 reiserfs defaults 0 2 
/dev/hda6 none swap sw 0 0 
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0 
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```

I have a backup of my /home directory, so that's not a big deal. But is there a way to fix this other than a total reinstall? I want hda6 for root and hda8 for /home. If I have to do a reinstall, what do I do differently when I do the manual partitioning?

UPDATE: I looked at my "Disk and Filesystems" section, and it looks there like my smaller partition (/hda6) IS / , while my /hda8 partition is just showing as /media/hda8. And if I go to /hda8/media/hda8/eric, I can see all my stuff.

So now I just need to know (I'm a n00b sorry) how to mount this correctly, so that /hda8 will be a regular ol' /home. Thanks!

---

### Post by twoseids on 2005-10-14
P.S. Here is my /etc/fstab from before my new installation: 
```

# /etc/fstab: static file system information. 
# 
# <file system> <mount point> <type> <options> <dump> <pass> 
proc /proc proc defaults 0 0 
/dev/hda6 / reiserfs defaults 0 1 
/dev/hda5 /boot ext3 defaults 0 2 
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0 
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0 
/dev/hda2 /media/windows ntfs ro,users,gid=users,umask=0002 0 0 
/dev/hda8 /home reiserfs defaults 1 2

``` 

If I just changed the pertinent partitions in my new /etc/fstab to reflect this, would that fix it?

---

