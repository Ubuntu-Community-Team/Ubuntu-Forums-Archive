---
title: "JFS in kernel 2.6.31-3 and higher"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nystire on 2009-07-25
Has JFS been moved from being part of the kernel to being a module? I noticed recently that I can no longer boot while my / partition is of type JFS. I get an error about VFS being unable to sync due to an unknown block type and the computer simply sits there flashing lights and looking pathetic.

---

### Post by taavikko on 2009-07-25
```
taavikko@hp-dv5:~$ grep -i jfs /boot/config-2.6.31-4-generic 
CONFIG_JFS_FS=m
CONFIG_JFS_POSIX_ACL=y
CONFIG_JFS_SECURITY=y
# CONFIG_JFS_DEBUG is not set
CONFIG_JFS_STATISTICS=y
```

```
taavikko@hp-dv5:~$ locate jfs
/boot/grub/jfs.mod
/lib/modules/2.6.31-2-generic/kernel/fs/jfs
/lib/modules/2.6.31-2-generic/kernel/fs/jfs/jfs.ko
/lib/modules/2.6.31-3-generic/kernel/fs/jfs
/lib/modules/2.6.31-3-generic/kernel/fs/jfs/jfs.ko
/usr/lib/grub/i386-pc/jfs.mod

```

---

### Post by nystire on 2009-07-25
Bugger.

Do you know where they discussed this? Maybe it was simply something which fell through the cracks and so can be reversed (I hope).

---

### Post by taavikko on 2009-07-25
> **nystire said:**
> Bugger.

Do you know where they discussed this? Maybe it was simply something which fell through the cracks and so can be reversed (I hope).

I have no recollection of any discussion of this (that doesn't imply that there was none).
Would be funny though module cannot be loaded until /lib is mounted which cannot be achieved until / is mounted :D

I would suggest reporting a bug against linux.

---

### Post by nystire on 2009-07-25
Reporting now :) I REALLY don't want to have to back up 750GB (I know. Bad partitioning scheme. Not my idea.) from the family's home server server and reinstall...

---

### Post by psyke83 on 2009-07-25
> **nystire said:**
> Reporting now :) I REALLY don't want to have to back up 750GB (I know. Bad partitioning scheme. Not my idea.) from the family's home server server and reinstall...

Not many people use JFS nowadays and is no longer directly maintained by IBM, so is it a good idea to continue advertising it as a supported filesystem for new users?

You can add the jfs module to /etc/initramfs-tools/modules, then run:
```
$ sudo update-initramfs -u
```

---

### Post by nystire on 2009-07-25
Bookmarked for future reference. However, I'm not too sure that will help me migrate off of JFS :) unless you know of any tools which can convert JFS->Something supported without needing to back everything up, format and restore afterwards.

---

