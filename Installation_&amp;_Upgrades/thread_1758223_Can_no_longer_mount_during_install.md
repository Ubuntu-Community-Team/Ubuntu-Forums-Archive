---
title: "Can no longer mount during install?"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by doglover56 on 2011-05-14
Hello.  In most of the previous versions of the installer, during partitioning you could take an existing partition, state the partition type, and manually type in a mount point, like /FAT32DATA and it would just show up in fstab and in the filesystem.  This appears to have been disabled in all the 11.04 variants that I have tried. You can no longer type in a mount point.  How come?  It was a convenient feature.
Thanks,
Irwin

---

### Post by Hedgehog1 on 2011-05-14
This is a bug that was found to late to be fixed before 11.04 was released.

The intent is for that functionality to be included in future releases again.

For now, please backup your old **/etc/fstab** file to someplace safe, and then copy the lines for your extra mounts back into the new **/etc/fstab** that is created by the install.

***The Hedge***

:KS

---

