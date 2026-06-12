---
title: "Repartitioning"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by satimis on 2012-08-23
Hi all,

Ubuntu 12.04 desktop 64bit
Fedora 17, 64bit
HD 160G

Ubuntu 12.04 has been installed on the HD first, several days ago, taking up the whole disc without partitioning. Later I added/installed Fedora 17 selecting the "Shrink" option with LVM partitioning and saved the bootloader on /dev/sda1 to make them dualboot. Installation was successful with dualboot option. Unfortunately by mistake I retained insufficient space for Ubuntu 12.04, only about 100M left when it is up.

Fedora 17 is on LVM partition but NOT Ubuntu 12.04


Then I took following steps to shrink /home of Fedora 17

# vgchange -a y
# resize2fs -f /dev/mapper/vg_fedora17-lv_home

# e2fsck -f /dev/mapper/vg_fedora17-lv_home```

e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/mapper/vg_fedora17-lv_home: 477/5070848 files (5.9% non-contiguous), 383520/20258816 blocks

```

# resize2fs /dev/mapper/vg_fedora17-lv_home 9G```

resize2fs 1.42 (29-Nov-2011)
Resizing the filesystem on /dev/mapper/vg_fedora17-lv_home to 2359296 (4k) blocks.
The filesystem on /dev/mapper/vg_fedora17-lv_home is now 2359296 blocks long.

```

# lvreduce -L 10G /dev/vg_fedora17/lv_home```

.....
Do you really want to reduce lv_home? [y/n]: y
  Reducing logical volume lv_home to 10.00 GiB
  Logical volume lv_home successfully resized

```

Now about 68G free space is available.  But I have no solution to resize / of Ubuntu 12.04 taking up the free space.

Please help.  TIA

B.R.
satimis

---

