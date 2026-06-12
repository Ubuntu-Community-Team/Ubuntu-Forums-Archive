---
title: "What's wrong with my fstab?"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by ppan76 on 2007-04-26
fstab line
# /dev/sda2
UUID=E7CA-08DE  /media/SHARED     vfat    defaults,utf8,umask=007,gid=46 0  1

fdisk -l 
/dev/sda2            3825       10091    50334921    e  W95 FAT16 (LBA)

Whenever I modify files on this FAT32 partition the files get corrupted. Sometimes when I copy files to the partition they dissappear after rebooting.  I think my fstab is wrong for this mount. Can anybody help me fix it? Thanks

----------------------------------------------------------
I just changed it to this
UUID=E7CA-08DE  /media/SHARED     vfat   defaults,utf8,fmask=0111,dmask=0000   0   0

Hope it works better.

---

### Post by hyperair on 2007-04-26
Strangely I remember having this problem back when I was using Dapper. The problem doesn't happen for me anymore. Wonder how I did that..

Anyway, here's the vfat line from my fstab.
/dev/hdb1 /media/hdb1 vfat defaults,utf8,umask=002,gid=46 0 1

---

### Post by ppan76 on 2007-04-26
> **hyperair said:**
> Strangely I remember having this problem back when I was using Dapper. The problem doesn't happen for me anymore. Wonder how I did that..

Anyway, here's the vfat line from my fstab.
/dev/hdb1 /media/hdb1 vfat defaults,utf8,umask=002,gid=46 0 1

Things seems to be improving a little.  WIth my new fstab the files dont get corrupted anymore. However they are not visible with Windows Vista until I scan the disk.  After scanning the disk, I can see the files with Windows Explorer.

Anybody have another line for me to try? this is so confusing.

---

### Post by hyperair on 2007-04-27
Here's a tip: if you hibernate one system and run the other, please stop doing that. You could seriously damage your hard disk. Not physically, but the data in it.

---

### Post by ppan76 on 2007-04-30
> **hyperair said:**
> Here's a tip: if you hibernate one system and run the other, please stop doing that. You could seriously damage your hard disk. Not physically, but the data in it.

Thanks. I think that was the problem.

---

