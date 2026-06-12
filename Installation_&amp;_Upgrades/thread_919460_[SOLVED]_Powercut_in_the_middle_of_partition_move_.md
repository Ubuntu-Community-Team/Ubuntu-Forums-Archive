---
title: "[SOLVED] Powercut in the middle of partition move and resizing"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by ad_267 on 2008-09-14
Ok so I finally got around to deleting my windows partition which was /dev/sda1 and moving and resizing my root partition /dev/sda2 to take up that space. But in the middle of the file system move there was a power cut and my computer shut down. I've attached a screenshot from gparted now and fdisk -l gives this:

```
$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60c260c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        2125    17061030   83  Linux
/dev/sda3            4605        4865     2096482+   5  Extended
/dev/sda5            4605        4865     2096451   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd99b3a6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 1027 MB, 1027416576 bytes
16 heads, 63 sectors/track, 1990 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1991     1003305    e  W95 FAT16 (LBA)
```

So what can I do? I haven't tried booting from the partition but I don't think that will work. It looks pretty messed up. All of my data is on another hard drive so I can reinstall everything if I have to but that would be a major pain and take a long time.

---

### Post by lisati on 2008-09-14
Other more knowledgable forum users might be able to help further, but from the screenshot it looks as if you might be able to try the resizing option again.

---

### Post by ad_267 on 2008-09-14
Yeah, but I think that would lose all the information there. I think what happened is that all my data is in the "unallocated" space and gparted was copying that to the end of the partition. So I want to resize the partition but I want it to use all the data in the unallocated space. I have a feeling I'm going to have to reinstall.

Is there somewhere that stores a list of packages I've installed so that I could try to recover that?

---

### Post by ad_267 on 2008-09-14
Think I'm just going to wipe that partition and reinstall. Oh well.

---

