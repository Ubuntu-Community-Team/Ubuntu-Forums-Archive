---
title: "How to mount harddrive using character iso8859-15 (latin ?) under Ubuntu ?"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by Fnx on 2008-06-19
Hello,
I have a *somewhat* old data harddrive which was formatted in Reiserfs, back in time where utf8 was not implemented (I guess it was using iso8859-15 latin character set). I am trying to mount it under Ubuntu with the correct character set specified so that european characters appear correctly.

My question is:
Are there options to pass to mount or in /etc/fstab to mount this harddrive ?

I know this is possible for FAT32 or NTFS filesystem with option iocharset (see below), but I cannot find working option for a ReiserFS.
```

> ets/fstab
# Partitions Windows - FAT32
/dev/sda1    /media/win       vfat    rw,user,auto,exec,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850,shortname=mixed        0       0

```

Thanks in advance for your help.

---

