---
title: "Ubuntu does not load after resizing"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by dev3 on 2007-10-10
hey!
I have been using 7.04, ever since it came out, without any problem. Last week I decided to resize the Ubuntu partition, and decrease it, since I dual boot with Xp, and for my work, I have to use some of Windows only programs, and I was running out of space.
So I resized the Ubuntu Partition and made a new Partition of 9.77Gb, (using Gparted on the live cd).

After this, I rebooted, but could not get into Ubuntu.  Grub works fine, then I can see the splash screen, but then I get this error message:
**[B]/bin/sh: can't access tty; job control turned off**[/B]

So I get into the Live cd, and this is what I get using fdisk
> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        7296    38122245    f  W95 Ext'd (LBA)
/dev/sda5            2551        3694     9189148+  83  Linux
/dev/sda6            4970        5100     1052226   82  Linux swap / Solaris
/dev/sda7            5101        7296    17639338+   b  W95 FAT32
/dev/sda8            3695        4969    10241406    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 256 MB, 256901120 bytes
256 heads, 56 sectors/track, 35 cylinders
Units = cylinders of 14336 * 512 = 7340032 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          35      250853+   6  FAT16

when I begin Gparted, I can see the orignal partition 
[IMG]http://www.bagthatpic.com/images/0040/GYh17256.png[/IMG]

but I get this error message as well
[IMG]http://www.bagthatpic.com/images/0040/IPI17309.png[/IMG]

When I am in Xp, I can see and extract the files on this partition using **explore2fs**


What should I do, to boot into linux? I really miss Ubuntu..and can't stand using Xp any more...

---

### Post by scrooge_74 on 2007-10-10
Check also what your original Grub says, remember you made a new partition and you could have affected GRUB

---

### Post by dev3 on 2007-10-10
Grub points to (hd0,4) as the root..
which I asume is sda 5....or am I wrong??

---

### Post by dev3 on 2007-10-10
does fstab have something to do with it??

---

### Post by scrooge_74 on 2007-10-10
> **dev3 said:**
> Grub points to (hd0,4) as the root..
which I asume is sda 5....or am I wrong??

I think in Grub the first number is 0 so i don't think it is counting the right way. Check[ this]("http://ubuntuforums.org/showthread.php?t=224351") thread it will probably give you an idea 

> **dev3 said:**
> does fstab have something to do with it??

In fstab you have all of your partitions declare so the system can read them.

---

