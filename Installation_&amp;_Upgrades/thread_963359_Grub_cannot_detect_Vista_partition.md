---
title: "Grub cannot detect Vista partition"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by crash91 on 2008-10-30
For a while now I've had Vista+XP dual booting, I decided to format the XP partition and replace with Ubuntu.
Grub automatically added an entry for "Windows XP embedded", this is the media direct partition on my dell, it did not detect vista.

fdisk -l output:
```
Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  de  Dell Utility
/dev/sda3               7       14409   115692097+   f  W95 Ext'd (LBA)
/dev/sda5            3271       10883    61151391    7  HPFS/NTFS *Documents Partition
/dev/sda6           14148       14409     2104483+  dd  Unknown
/dev/sda7           10884       14147    26218048+   7  HPFS/NTFS *Vista Partition
/dev/sda8            3146        3270     1003999+  82  Linux swap / Solaris
/dev/sda9               7        3145    25213954+  83  Linux
```

What do I need to edit my menu.lst to so it boots Vista?
(hd0,5) was the one for /dev/sda6 so (hd0,6) would be vista, when I try to edit that at boot time it give me the error: 
```
error 12 -  Invalid device requested
```

menu.lst part:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title		Microsoft Windows XP Embedded
root		(hd0,5)
savedefault
makeactive
chainloader	+1
```

---

### Post by crash91 on 2008-10-30
*bump*
Help please.

---

### Post by caljohnsmith on 2008-10-30
Somehow your Vista ended up in a logical partition, and normally Windows will not boot directly from a logical partition; if you install Windows to a logical partition, it will usually put its boot files in some FAT/NTFS primary partition. Since you installed Vista after XP, your Vista boot files were most likely in the XP partition, so when you deleted XP, you can't boot Vista now.

The good news is that it is possible to boot Vista directly from a logical partition, i.e. have all of Vista's boot files in the logical partition, but it takes a little bit of work. You will need to start by reinstalling your Vista boot files to the Vista partition. Forum member meierfra has a great guide for booting Vista from a logical partition, and you can read his guide [here]("http://ubuntuforums.org/showthread.php?t=813628") (see post #4). If you want help with it, then first post:
```

sudo mount /dev/sda7 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L, not a one. We can work from there if you would like help. :)

---

### Post by crash91 on 2008-10-30
Aha! so thats the problem, I had a feeling I rushed the install a bit this time :) 
Thanks a lot! I'm going to do the lats few steps now, I'll tell you how it goes.

EDIT: It worked :) I had a few problems because vista suddenly became deactivated and i had to reactivate. There is still a "This copy of Window is not genuine" watermark on my desktop, although it works fine.

---

