---
title: "Feisty: fsck error regarding /dev/.tmp-254-0"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by gspr on 2007-04-20
Hi.

Yesterday I upgraded to Feisty. Roughly every third of fourth time I boot, I get the following fsck error:
```
Log of fsck -C -R -A -a
Fri Apr 20 09:52:48 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/.tmp-254-0
/dev/.tmp-254-0:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Fri Apr 20 09:52:48 2007
----------------

```

Hitting control-d to continue booting works fine.

Any ideas?

---

### Post by pepsi_max2k on 2007-04-20
See this thread regarding a problem i had with fsck during suse boot after altering partitions to install ubuntu:

[http://forums.suselinuxsupport.de/index.php?showtopic=30746&pid=227833&st=0&#entry227833](http://forums.suselinuxsupport.de/index.php?showtopic=30746&pid=227833&st=0&#entry227833)

It may be kinda similar, then again may be nothing to do with it :popcorn:

---

### Post by gspr on 2007-04-23
Thanks for the idea. Sadly, it doesn't seem to be the case.

Any more ideas? I find it so strange, especially since this appears to happen only in about 1 boot out of 5.

---

### Post by Calavera07 on 2007-04-26
I have the same problem, except that the filename is  /dev/.tmp-254-3

---

### Post by gspr on 2007-04-27
I tried going to maintenance mode when this happened, and I can't find any reference to any /dev/.tmp-* anywhere.

---

