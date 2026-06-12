---
title: "Unable to Mount NTFS drives"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by shoaibi on 2007-11-09
I'm trying to mount NTFS drives on Ubuntu using:

/dev/sda7	/media/Others	ntfs		nls=utf8,umask=0222	0	0

but this gives error and suggests:

/dev/sda7	/media/Others	ntfs-3g		defaults,forced	0	0

but this results up with automatic unmount after a little while...
need some help for this.

---

### Post by bulldog on 2007-11-09
In my fstab looks a mount point for an NTFS partition like this```

# Entry for /dev/sdb1 :
UUID=10B45E06B45DEEAA /media/sdb1 ntfs-3g defaults,locale=nl_NL.UTF-8 0 1
```

My language is Dutch so ignore that.
To find your uuid for the partition```
ls /dev/disk/by-uuid -lh
```

---

