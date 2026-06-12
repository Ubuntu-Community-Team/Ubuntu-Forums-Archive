---
title: "Installer won't detect root"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by paritosh1010 on 2007-01-20
I am trying to use the liveCD for Edgy installation, and I use the installer present on the desktop for installation. I choose the Manual Partition method, and It shows the page where we have to select the mount points.

I select the mount point of / to /dev/hda3 with Reformat option and mountpt of swap to /dev/hda6. When I click forward, it says No rootfilesystem detected.

/dev/hda3 is formatted as ext2.
Any help?

---

### Post by egon123 on 2007-01-21
There is some bug in the installer for reiserfs-partitions.
The installer will only detect ext-partitions, no reiserfs.
My solution:
sudo gparted

format your partition with "ext3"

now the installer will detect the partition as root, and in my case it even did a reiserfs-format, when i checked "format partition"


Egon

---

### Post by paritosh1010 on 2007-01-21
My partition is ext2. Shouldn't it detect it automatically? The Dapper LiveCD did detect the same partition.

---

