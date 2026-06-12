---
title: "grub error getting windows to show up"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by Brizzle on 2007-07-09
i'm having a hard time getting windows to show up in grub.

before:
i had xp pro, vista rc1 and ubuntu on 3 partitions on the same disk. grub used to load, and give me the ubuntu options and a windows loader option.  the windows loader would then let me pick vista or xp.

i decided to make the rc1 partition into fat32 storage for my xp and ubuntu to share, and to reinstall an up-to-date ubuntu in the process.

here's my new fdisk output
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       12161    97683201    f  W95 Ext'd (LBA)
/dev/sda5            5738        8924    25599546    7  HPFS/NTFS
/dev/sda6            8925        9173     2000061   82  Linux swap / Solaris
/dev/sda7               1        5737    46082358    b  W95 FAT32
/dev/sda8            9174       12161    24001078+  83  Linux

Partition table entries are not in disk order
```

as you can see, /dev/sda5 is the XP partition.

problem is grub only gives me the ubuntu options to choose from.

so i added this to the end of my menu.list

```
title           Microsoft Windows XP Pro
rootnoverify    (hd0,4)
savedefault
makeactive
chainloader     +1
```

but selecting the new xp option in grub gives me error "12 : Invalid device requested."

is there something i'm missing?

---

### Post by Odrodzona-Sarmacja on 2007-07-09
> **Brizzle said:**
> 
here's my new fdisk output
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       12161    97683201    f  W95 Ext'd (LBA)
/dev/sda5            5738        8924    25599546    7  HPFS/NTFS
/dev/sda6            8925        9173     2000061   82  Linux swap / Solaris
/dev/sda7               1        5737    46082358    b  W95 FAT32
/dev/sda8            9174       12161    24001078+  83  Linux

```
as you can see, /dev/sda5 is the XP partition.
```
title           Microsoft Windows XP Pro
rootnoverify    (hd0,4)
savedefault
makeactive
chainloader     +1
```
but selecting the new xp option in grub gives me error "12 : Invalid device requested."
is there something i'm missing?


Sure you are missing the right number for rootnoverify. Try (hd0,1) instead of (hd0,4), as your sda5 is number 2 partition in the row on this drive (from 5738 to 8924 is the second partition on this hd as you can see). It is not number fifth. :) just edit /boot/grub/menu.lst and correct it. It should fix the problem.

---

### Post by Brizzle on 2007-07-09
i tried (hd0,1) but it gives the same error.  i even made it (hd0,0) for the heck of it, and it told me the partition didn't exist so i think (hd0,4) is correct as far as i can tell.

the ubuntu blocks in my menu.list use (hd0,7) and as you can see its /dev/sda8

---

### Post by merlinus on 2007-07-09
I do not see from your fdisk output that any of your partitions are marked as bootable.

You can use gparted to set a boot flag on your windows partition, and perhaps that will help.

-merlin

---

### Post by Odrodzona-Sarmacja on 2007-07-09
Surely you should set it as boot (it shoudl be marked with * in fdisk) and also did you try (0,5) by any chance too ? ;)

---

### Post by Brizzle on 2007-07-09
i used gparted to set the xp partition to bootable (shows a * in correct column now in fdisk) and i still get the same error. :(  for a second i really thought that may have been what i was forgetting.

i've tried hd0,5 a few times for the hell of it and get the same error.

i'm starting to wonder if it isn't a larger issue with how/where grub is installed.


and i wonder if it has something to do with how it worked originally.  i first had to install vista, then xp.  at that point the *windows loader* let me choose vista or xp.
after that i installed ubuntu.  grub pointed to either ubuntu or the *windows loader*.  and the *windows loader* to either vista or xp.

get it? :P

grub -> windowsLoader, Ubuntu
windowsLoader -> vista, xp

now windowsLoader is gone basically (i think it disappeared when i turned the vista partition into that fat32).  and i cant link up grub -> xp, ubuntu for some reason.

would it help to completely uninstall/reinstall grub?

---

### Post by Bothered on 2007-07-09
Have you tried (hd0,2)?

---

### Post by Odrodzona-Sarmacja on 2007-07-10
> **Brizzle said:**
> 
grub -> windowsLoader, Ubuntu
windowsLoader -> vista, xp

now windowsLoader is gone basically (i think it disappeared when i turned the vista partition into that fat32).  and i cant link up grub -> xp, ubuntu for some reason.

would it help to completely uninstall/reinstall grub?

No. you don't need to change grub.

It is not grub's error, which doesn't let windows to show up. It is windows error.

What you need is to get that (hd0,4) windows xp partition bootable as vista partition was.  Obviously you need to get windows partition program to do the job correctly for windows os.

---

