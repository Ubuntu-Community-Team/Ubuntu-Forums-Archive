---
title: "Clone Ubuntu Physical Drive"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by Vectorferret on 2010-06-27
My Ubuntu system drive is starting to throw up S.M.A.R.T. errors. I have two partitions on the drive (/home and /) and grub in the mbr. Is there a way to exactly clone this drive to another one so I don't need to reinstall or re-setup anything?

---

### Post by b0b138 on 2010-06-27
ghost for linux   [http://sourceforge.net/projects/g4l/](http://sourceforge.net/projects/g4l/)    just burn the image to a disk and boot to it.

or the dd command run from the live cd. in this example sda is the source/old drive and sdb is the target/new drive
```
dd if=/dev/sda of=/dev/sdb bs=16384 conv=notrunc,noerror
```

---

