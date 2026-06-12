---
title: "Dual Boot to finish XP install"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by edbyford on 2007-09-26
Hi all

Just trying to install XP on my Ubuntu machine. I made an 8GB partition, then I started the XP install. After a bit, the install restarted and my machine wouldn't boot, because Windows had overwritten GRUB. So, I restored Grub and added the XP partition to the menu.lst. But when I try and boot it, it says 'Disk error - no bootable disk' (or similar).

Have I done it right? Below is what happens when I do 'fdisk -l /dev/sda'
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       59031   474166476   83  Linux
/dev/sda2   *       59032       60051     8193150    b  W95 FAT32
/dev/sda3           60052       60801     6024375    5  Extended
/dev/sda5           60052       60801     6024343+  82  Linux swap / Solaris
```

Then what I added to the very end of my menu.lst:
```
title        Microsoft Windows XP
root        (hd0,1)
makeactive
chainloader    +1
```

P.S. The XP installation hasn't finished yet...obviously normally it would boot the cd, copy some files, then restart and boot from the hard drive to continue the install, so I thought that's what I need to do...

---

### Post by rsambuca on 2007-09-26
You might try 'rootnoverify' instead of 'root' for XP, although it is pretty hard to tell what is or isn't working if you haven't finished installing it yet!

Why are you using FAT32 by the way.  It is really not a very good file system.

---

### Post by edbyford on 2007-09-26
Basically I think I put the wrong numbers in (hd0,1) but I'm not sure.

I'm using FAT32 to ensure that it's backwards compatible.

I don't think the error message has anything to do with XP, it's either a message from GRUB or my mobo. the same message appeared after XP overwrote my GRUB (so then I restored GRUB).

---

### Post by rsambuca on 2007-09-26
If you have one hard drive, then hd0,1 is correct.  XP really likes to be on the first partition, though, so that could be an issue as well.

I still think FAT32 is a bad idea!  At least use ntfs.

---

### Post by Martin Witte on 2007-09-26
common practice is to first install windows, then linux - see [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot).

---

