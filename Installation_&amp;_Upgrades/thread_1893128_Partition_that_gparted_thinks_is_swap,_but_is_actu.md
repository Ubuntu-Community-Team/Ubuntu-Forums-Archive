---
title: "Partition that gparted thinks is swap, but is actually mounted as ext3"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by samcan on 2011-12-09
I'm trying to migrate to Ubuntu from Arch Linux, but I have a screwed-up home partition that I think is getting in the way.

When I boot into the Ubuntu live CD, ubiquity and gparted both think that my home partition uses the swap filesystem. However, when I mount the partition in the file manager and browse my files, mount says it's using ext3.

```

/dev/sdb1 on /media/c8220805-2640-4ed6-86b1-3dc5b09cb01a type ext3 (rw,nosuid,nodev,uhelper=udisks)

```

Is there anything I can do to fix this without losing my files?

Thanks!

---

### Post by editheraven on 2011-12-09
You can try

sudo fdisk /dev/sdb > t > 1 > 32


Anyway, gparted is giving some false alerts sometimes. You can try and resize your ext3 partition, so mbr code will be updated.

---

### Post by oldfred on 2011-12-09
swap has no format.

Do you have UUID or /dev/sdXY mixed up between /home and swap?

---

