---
title: "Yet another fsck problem"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by ghotra on 2007-05-15
It seems lots of people have been having fsck problems with feisty...was there something wrong with the release?

Anyway, I am getting the following:


```

fsck.ext3: Bad magic number in super-block while trying to open /dev/sdd1
/dev/sdd1
The superblock could not be read or does not describe a correct ext2 filesystem
......

```

Blah blah...ok....the error makes sense because /dev/sdd1 is NOT an ext filesystem----it is an ntfs partition!  So why is it even being checked?  Help please.

Here is my fstab line:

```

# /dev/sdd1
UUID=1056044E563322F9 /media/sdd1   ntfs   defaults,nls=utf8,umask=007,gid=46  0  1
# /dev/sdd3

```

And I am worried the same will happen with /dev/sdd3 which is vfat.

Annoyed.

---

### Post by kidders on 2007-05-16
Hi there,

That's freaky! My temptation is to be distrustful, and ask for the output of **ls -l /dev/disk/by-uuid**, just to be certain that the line you posted from your /etc/fstab does in fact describe /dev/sdd1.

Realistically though, I doubt you would have made such a mistake. Perhaps you should log a bug report.

In terms of safety, you shouldn't need to worry ... **fsck** shouldn't damage your filesystems. This glitch is still intolerable though! Do you have ntfsprogs installed?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

