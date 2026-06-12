---
title: "Problem with FSTAB"
date: 2005-03-24
forum: Installation &amp; Upgrades
---

### Post by audax321 on 2005-03-24
Hello,

  I'm trying to get my other partitions to work with Ubuntu and here is what I have added to /etc/fstab:

/dev/hda1       /mnt/windows/C  ntfs    ro,gid=users,umask=0002,users 0 0
/dev/hdb1       /mnt/windows/D  vfat    defaults,gid=users,umask=000700,users 0 0

The first drive seems to work fine... I can access it and not write to it (because its ntfs).

The second drive is kind of working... I can write to some directories, but not all, but I have read access to all.

I searched the forums and google and tried everything, but other solutions seem to completely make the drive either unreadable or unmountable. Any suggestions?

---

### Post by Buffalo Soldier on 2005-03-24
Have you tried?```
/dev/hda1       /mnt/windows/C    ntfs    umask=0222      0       0
/dev/hdb1       /mnt/windows/D    vfat    umask=000       0       0
```

---

### Post by audax321 on 2005-03-24
Okay, that is definitely better, but there are still one or two folders with a lock icon in Nautilus that I don't have write access to. Any more ideas?

---

