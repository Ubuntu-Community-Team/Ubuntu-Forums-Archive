---
title: "Raid Disk Replaced"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by xMbx on 2007-06-22
Hello,

i used the common Ubuntu Software Raid 1. No one drive got damaged and needed to be replaced.

So, what todo now, to get Raid complete again ? Currently running only on one drive. Thanks.

---

### Post by xMbx on 2007-06-23
Helllllppppppp neeeded.

---

### Post by Pumalite on 2007-06-23
> **xMbx said:**
> Helllllppppppp neeeded.

Read this; it might help:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by xMbx on 2007-06-25
So, i managed now to replace the disk and get the raid working, but... 

i still get an error when filecheck looks for stuff at the startup:

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

i assume, i that is a problem regarding the boot partition.

How to fix that ? Could anybody at least help with that... thanks.

---

