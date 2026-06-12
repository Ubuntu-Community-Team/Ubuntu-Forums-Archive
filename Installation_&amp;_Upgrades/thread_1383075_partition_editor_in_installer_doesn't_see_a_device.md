---
title: "partition editor in installer doesn't see a device"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by Jguy on 2010-01-16
Well, I figured I would give KDE another try, it's been a while since I've used it and looks a little sexy.

Anyway, I have four different hard drives on my machine, namely /dev/sda, /dev/sdb, /dev/sdc and /dev/sdd. fdisk on the livecd confirms this:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73557355

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a0f81

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fb1c96d

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x367a3679

   Device Boot      Start         End      Blocks   Id  System

```

I need to specify partitions manually because /home is going on sdb and kubuntu installs to sda. However, the installer does not detect I have an sda. The list just goes something like this:

/dex/sdb
/dev/sdc
/dev/sdd

in gparted I am also able to delete and add partitions to /dev/sda, and even if I were to add the partitions manually to sda in gparted, the installer for kubuntu still does not see that whole device.

Any ideas?

thanks.

---

