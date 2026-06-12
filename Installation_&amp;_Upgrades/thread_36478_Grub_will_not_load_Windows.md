---
title: "Grub will not load Windows"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by davidmigl on 2005-05-23
Hi all,

I installed Ubuntu a few weeks ago and am liking it.  One of the issues that came up immediately after installation was that the Grub bootloader would not load Windows 2000 (on a separate had drive).  When I selected in the menu to boot to windows, all I would get was ```
Booting "Microsoft Windows 2000 Professional"

root (hd1,0)
     Filesystem type unknown, partition type 0x?
savedefault
makeactive
chainloader +1
```

Now this has not been a problem, as I could simply change the HDD boot priority in the BIOS to boot successfully into windows.  But Grub surely should be able to boot to windows, and I would like to set this up so you do not have to change boot priority.  When Grub offers to boot into Windows, why doesn't it?

---

### Post by jkndrkn on 2005-05-23
Boot into linux and try editing your grub menu:

```
sudo pico /boot/grub/menu.lst
```

Try changing your entry for windows:

```

title           Windows XP
rootnoverify	(hd1,0)
makeactive
chainloader	+1

```

Make sure rootnoverify (hd1,0) is pointing at the correct partition.
i.e. if windows is in the first partition of hdb, change to (hd2,0)

Take a look at this post:

[http://www.ubuntuforums.org/showpost.php?p=178124](http://www.ubuntuforums.org/showpost.php?p=178124)

---

