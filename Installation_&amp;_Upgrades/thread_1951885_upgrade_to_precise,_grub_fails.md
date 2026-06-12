---
title: "upgrade to precise, grub fails?"
date: 2012-04-03
forum: Installation &amp; Upgrades
---

### Post by metalfan_ on 2012-04-03
```

Setting up grub-common (1.99-20ubuntu1) ...
Setting up grub2-common (1.99-20ubuntu1) ...
Setting up grub-pc-bin (1.99-20ubuntu1) ...
Setting up grub-pc (1.99-20ubuntu1) ...
/usr/sbin/grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: non-sector-aligned data is found in the core file.

```

what might be the problem?
grub worked before and i did not change grub related config files.

---

### Post by darkod on 2012-04-03
Are you using gpt table on the HDD, or did you use gpt earlier? That message about post-MBR is weird.

Also, this might be due to the fact that 12.04 is not released yet. It is never recommended to use development version as your main system.

---

### Post by oldfred on 2012-04-03
Does your first partition start at a non-standard location. Old systems used sector 63 as the first and new systems use sector 2048 as the first sector leaving lots of room for grub and windows to install stuff (technical term) in the 'unused' ares.

Post this:
```

sudo fdisk -lu
```

---

### Post by metalfan_ on 2012-04-03
i guess the system was first installed with ubuntu 8.04 but im not sure.
nothing besides what ubuntu uses for partitioning touched the drive.

```

sudo fdisk -lu
[sudo] password for julius:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc87ec87e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1   163846934    81923467   83  Linux
/dev/sda2       163846996   311516414    73834709+   5  Extended
/dev/sda5       163846998   164826899      489951   82  Linux swap / Solaris
/dev/sda6       164826963   289844729    62508883+  83  Linux
/dev/sda7       289844793   311516414    10835811   83  Linux

```

---

### Post by darkod on 2012-04-03
sda1 start sector is 1. It didn't leave any space at all at the front of the disk.

As oldfred said, earlier the first partition was starting at sector 63, these days it starts at 2048.

I have never seen a disk where it starts at 1.

Maybe shrinking sda1 a little bit at the front?

---

### Post by metalfan_ on 2012-04-04
is that even possible when the system is running on sda?

---

### Post by darkod on 2012-04-04
Nope, you could only run it from live mode.

Of course, the same as any partition procedure, it does carry small risk that something gets corrupted, but in most cases it works out fine. It's best to have a full backup before doing it anyway.

---

### Post by metalfan_ on 2012-04-04
any idea how i could get a old static grub that can be installed just in case?

---

