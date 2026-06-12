---
title: "boot-repair wont reinstall grub"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by JohannesJo on 2011-10-29
Having quite some trouble with ubuntu and my partitions ([http://ubuntuforums.org/showthread.php?t=1871934](http://ubuntuforums.org/showthread.php?t=1871934)) I tried to use boot-loader. But somehow it seems that it cant access my linux partition and if I use it anyway my recovery partition loads afterwards.

In Advanced-Mode it looks like this
(picture of the first panel with grub/features not existent or or deactivated.  will be provided very soon.)


Shouldnt it look like this
[http://ubuntuforums.org/showthread.php?t=1769482&highlight=%40boot-repair+reinstall+grub+bootloader%40](http://ubuntuforums.org/showthread.php?t=1769482&highlight=%40boot-repair+reinstall+grub+bootloader%40)

---

### Post by raja.genupula on 2011-10-30
Hi man , 

     Boot from live cd and then install the grub to your harddisk by using this cd 

```
sudo dpkg-reconfigure grub-pc
```

all the best man.

---

