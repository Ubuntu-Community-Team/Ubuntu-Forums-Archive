---
title: "Migrating RAID5 and LVM from another distribution"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by kleptophobiac on 2009-11-15
I'm jumping ship from Arch Linux to Ubuntu for a lot of reasons. AL's package management system used to be stellar, but is getting a little bit rough around the edges. I'm also looking to turn a computer into a combination of server and desktop, and the desktop experience with Ubuntu appears much better than with other distributions.

In any case, the machine that I'm running has three WD hard drives in it that are in a RAID5 array. On top of that, I use LVM to be more flexible about partition management. Right now I'm dual booting Arch Linux and Ubuntu while I get used to the new environment and to help ease the migration from one system to another.

The RAID5 array has been detected OK, using the same set of drives. For some reason it wanted to rebuild my spare, but I went ahead and let it go. Nothing bad seemed to come of it. My Arch Linux install still reads the RAID5 nicely. But I seem incapable of getting pvscan to detect the LVM physical volume on the RAID5 array. I know it's there - Arch Linux still finds it - but I can't seem to make the same magic happen in Ubuntu.

Both of the distributions have a nearly identical default /etc/lvm/lvm.conf that allows the use of md? devices.

```
root@tungsten:~# pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  No matching physical volumes found
root@tungsten:~# 
```

This is on a fresh install of Ubuntu 9.10 - Karmic Koala. Any insight into the issue would be greatly appreciated. Let me know if there's any useful information I can add to help this make more sense.

Thanks a bunch!
-Sasha

---

### Post by kleptophobiac on 2009-11-16
Some more information that I think may be useful/interesting. Under Archlinux when I print the partitions on /dev/md0, it shows that there are none and that everything is free space. Under Ubuntu, it detects a partition that is half of the array size... or about 1TB.

That the partition information on the RAID5 array is being misread under Ubuntu suggests that perhaps it hasn't reassembled it correctly and that the data it's reading is garbage. Is there a way to verify and correct that?

Thanks for the help!

---

