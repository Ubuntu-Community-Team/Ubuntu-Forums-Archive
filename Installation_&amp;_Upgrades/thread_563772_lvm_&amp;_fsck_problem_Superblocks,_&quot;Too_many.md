---
title: "lvm &amp; fsck problem: Superblocks, &quot;Too many levels of symbolic links&quot;"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by HuG on 2007-09-30
UPDATE: This problem vanished after changing to standard (2.6.22-12-generic) kernel (from 2.6.20-16-lowlatency by ubuntustudio.net). I'm using "Ubuntu gutsy (development branch)".


Hey,

I "lost access" to my home lvm partition. I had to reboot (alt-ctrl-del) because of a halted X server (radeon driver; vesa works). The umount on that occasion wasn't propably clean. Too bad.

I'm now not sure where the problem is, with lvm or ext3, nor how to fix it. The error message isn't particularily helpful with my knowledge.

This is the error message I get: 

```

root@1gu:~# fsck.ext3  /dev/vg0/home 
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Too many levels of symbolic links while trying to open /dev/vg0/home

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@1gu:~# e2fsck -b 8193  /dev/vg0/home 
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Too many levels of symbolic links while trying to open /dev/vg0/home

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```


Some data of my lvm setup:

```


root@1gu:~# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "vg0" using metadata type lvm2

root@1gu:~# lvm pvscan
  PV /dev/sdb3   VG vg0   lvm2 [288.73 GB / 0    free]
  Total: 1 [288.73 GB] / in use: 1 [288.73 GB] / in no VG: 0 [0   ]

root@1gu:~# lvscan 
  ACTIVE            '/dev/vg0/root' [6.84 GB] inherit
  ACTIVE            '/dev/vg0/swap' [200.00 MB] inherit
  ACTIVE            '/dev/vg0/home' [281.70 GB] inherit

root@1gu:~# lvm pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdb3
  VG Name               vg0
  PV Size               288.73 GB / not usable 1.18 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              73914
  Free PE               0
  Allocated PE          73914
  PV UUID               efGisg-7TRY-Xpjm-xenF-HYgl-s1PD-QkkDEm


```

I'm thankful of any help or specific pointers to additional relevant information (on lvm).

--
Janne

---

