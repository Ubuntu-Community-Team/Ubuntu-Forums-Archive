---
title: "unabridge boot disk available?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by willnight on 2006-07-03
i installed winxppro after ubuntu.

i can no longer use grub. i searched around: the recommended thing to do is to use ubuntu boot disk and use rescue mode to reset grub.

i don't have the boot disk while travelling. is there a "skeleton" version of a boot disk for download? i'm too impatient to download 700mb using slow connection.

or is there another way to fix this?

thnx.

---

### Post by confused57 on 2006-07-03
[QUOTE=willnight]i installed winxppro after ubuntu.

i can no longer use grub. i searched around: the recommended thing to do is to use ubuntu boot disk and use rescue mode to reset grub.

i don't have the boot disk while travelling. is there a "skeleton" version of a boot disk for download? i'm too impatient to download 700mb using slow connection.

or is there another way to fix this?

thnx.[/QUOTE]

If you installed Windows on a partition after Ubuntu, i.e. Ubuntu on the 1st partition and Windows on the 2nd partition, you probably won't be able to get a dualboot to work...Windows just about has to be the first OS in your partition tables.
If you installed Windows on a partiton before the Ubuntu partition, you can recover grub using the LiveCD:
[http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

Here are some boot disks, haven't tried them myself:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
[http://www.bootdisk.com/](http://www.bootdisk.com/)
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

Some people have suggested xosl:
[http://www.ranish.com/part/](http://www.ranish.com/part/)

---

### Post by RRS on 2006-07-03
I see confused57 has already given you the link to Ultimate boot disk but you might also want to check out [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") and [Damn Small Linux]("http://damnsmalllinux.org/").

DSL should give you the same repair options as Ubuntu live from it's terminal besides providing a full Linux OS until you have time to restore grub.

---

