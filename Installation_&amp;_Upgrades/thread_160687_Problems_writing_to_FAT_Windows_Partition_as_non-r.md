---
title: "Problems writing to FAT Windows Partition as non-root user"
date: 2006-04-15
forum: Installation &amp; Upgrades
---

### Post by tigr10 on 2006-04-15
Installed Ubuntu 5.10 the other day.  I'm having a problem mounting my windows partition(s).  I started with /dev/hda1.  It mounts at /media/hda1, but I need to sudo in order to write to it.  The non-root user gets a "Permission denied" error.

fstab is as follows:
proc                /proc              proc    defaults        0       0
/dev/hda7       /                     ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1  vfat     rw,user,uid=1000,umask=000       0
 0
/dev/hda2       /media/hda2     vfat    defaults        0       0
/dev/hda3       /media/hda3     vfat    defaults        0       0
/dev/hda5       /media/hda4     vfat    defaults        0       0
/dev/hda6       /media/hda5     vfat    defaults        0       0
/dev/hda8       none                 swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I want to be able to write to the partition as a non-root user as well.  Please advise what I am doing wrong.

---

### Post by stoeptegel on 2006-04-15
Replace the /dev/hda1 line with
```

/dev/hda1       /media/hda1  vfat    iocharset=utf8,umask=000   0       0

```

Note that ALL users have unlimited read/write access from bootup on hda1 this way.

---

### Post by aysiu on 2006-04-15
stoeptegel's suggestion has always worked for me. Though, I think your line should also work: ```
/dev/hda1 /media/hda1 vfat rw,user,uid=1000,umask=000 0 0
``` The only thing I can think of is that sometimes the /media directory (or /mnt directory) is not the most reliable mount place in terms of permissions.

You can try doing a static mount point: ```
sudo umount /media/hda1
sudo mkdir /data
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Replace your line with ```
/dev/hda1 /data vfat iocharset=utf8,umask=000 0 0
``` Control-x, y, Enter. ```
sudo mount -a
```

---

### Post by tigr10 on 2006-04-16
[QUOTE=stoeptegel]Replace the /dev/hda1 line with
```

/dev/hda1       /media/hda1  vfat    iocharset=utf8,umask=000   0       0

```

Note that ALL users have unlimited read/write access from bootup on hda1 this way.[/QUOTE]

This worked.  Thank-you very much.  I will use aysiu's notes if I have further problems re: mounting outside of /media

---

