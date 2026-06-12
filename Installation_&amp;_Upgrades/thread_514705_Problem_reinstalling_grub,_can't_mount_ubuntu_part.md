---
title: "Problem reinstalling grub, can't mount ubuntu partition"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by expertninja on 2007-08-01
After about 8 bluescreens in windows, I ended up reinstalling it to start with a fresh slate. I knew this would overwrite grub with the windows boot loader, but I figured I could reinstall it without too much of a hassle. However, the ubuntu 7.04 install disk won't mount the partition ubuntu was installed in. The partition manager simply freezes up, and I tried an older 6.06 install disk and the same problem happens. The file system is JFS.

---

### Post by logos34 on 2007-08-01
you can restore grub without having to mount root partition (which is necessary if you use the 'grub-install' method).  [Use this howto.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=catlett")

---

### Post by MQMike on 2007-08-01
Yes, I agree.  Easily, in fact.

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)


Look for the part called re-installing GRUB, with:
root (hdx, y)
setup (hd0)
quit
where (hdx, y) is your Ubuntu partition.  Hard drives and partitions are counted starting from zero. 
So, for example, (hd0, 1) is the first hard drive hd0, the second partition (that’s the “1”).

---

