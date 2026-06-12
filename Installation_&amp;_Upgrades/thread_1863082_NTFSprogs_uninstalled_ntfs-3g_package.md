---
title: "NTFSprogs uninstalled ntfs-3g package"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by razor7 on 2011-10-17
Hi, after installing ntfsprogs package, the package uninstalls ntfs-3g thus can't mount my ntfs partitions through fstab

I have this line in fstab that obiously does not work

UUID=6B3962A91560C093 /media/Data ntfs-3g defaults 0 0

Also this line does not work
UUID=6B3962A91560C093 /media/Data fuse.ntfs locale=es_ES.utf8 0 0

Any workaround?

Thanks a lot!

---

### Post by raja.genupula on 2011-10-17
Hi look at that them , follow the instructions to mount your ntfs partitions.

[http://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions](http://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions)

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

all the best.

---

### Post by razor7 on 2011-10-17
Hi, thanks for the reply, but i think my post is quite self explanatory.

Ubuntu 11.10 for some reason uninstalls ntfs-3g package when you install ntfsprogs package. Since that forced uninstallation, this line does not works anymore in fstab
> 
UUID=6B3962A91560C093 /media/Data ntfs-3g defaults 0 0

So...how can I mount my ntfs partitions at boottime (fstab) with ntfsprogs package installed?

Thanks in advise!

---

### Post by raja.genupula on 2011-10-17
> **razor7 said:**
> Hi, after installing ntfsprogs package, the package uninstalls ntfs-3g thus can't mount my ntfs partitions through fstab

I have this line in fstab that obiously does not work

UUID=6B3962A91560C093 /media/Data ntfs-3g defaults 0 0

Also this line does not work
 UUID=6B3962A91560C093 /media/Data fuse.ntfs locale=es_ES.utf8 0 0

Any workaround?

Thanks a lot!
```
/dev/hda1 /mnt/ntfs fuse.ntfs **locale=es_ES.UTF-8** 0 0
```
place ' - 'there after utf and try again (bold area)

all the best.

---

