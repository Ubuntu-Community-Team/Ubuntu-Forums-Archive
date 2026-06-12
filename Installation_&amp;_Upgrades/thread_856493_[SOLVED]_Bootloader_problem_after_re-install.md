---
title: "[SOLVED] Bootloader problem after re-install"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by GandalfNK on 2008-07-11
Hi there,

I have just re-installed Ubuntu on my computer, and now I'm having a bit of trouble getting it to boot the way I want.

Before the re-install, I used LILO to dual-boot Windows 2000 and Dapper. When I installed Hardy and had it install Grub I assumed it would just overwrite the old LILO configuration, but it didn't: the old LILO still loads when I boot normally. Now, obviously the kernel that the old LILO wants to load no longer exists, so the boot process just stops at some point.

I'm able to avoid the problem by booting into the menu of the Ubuntu installation CD and having it "Boot from first hard-disk", which then takes me to the expected Grub menu that contains my new Ubuntu install as well as Windows (which I upgraded to XP along the way).

I'm not much of an expert in using either Grub or LILO, so can anyone here please tell me how to fix this mess? Circumventing the faulty LILO by booting from the installation CD every time is not really a long-term solution, I'm afraid.

Cheers.

---

### Post by confused57 on 2008-07-11
You may be able to use the Ubuntu live cd to install grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by GandalfNK on 2008-07-11
Thanks, partial success, so far: I get to the correct grub boot menu now, and Ubuntu boots without problems. Unfortunately, Windows won't boot at all. I don't even get an error message after choosing to boot Windows, I just get a screen saying "Starting up..." and a rapidly blinking cursor.
Any clues?

---

### Post by confused57 on 2008-07-11
> **GandalfNK said:**
> Thanks, partial success, so far: I get to the correct grub boot menu now, and Ubuntu boots without problems. Unfortunately, Windows won't boot at all. I don't even get an error message after choosing to boot Windows, I just get a screen saying "Starting up..." and a rapidly blinking cursor.
Any clues?
You could post the output of:
```
sudo fdisk -l
```
-l is a small "L"
and
```
gedit /boot/grub/menu.lst
```

It may be necessary to use Lilo?:
[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)

---

### Post by GandalfNK on 2008-07-12
Okay, here's my partition table:
```
sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3d0d3d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sda2            1531        4864    26780355    f  W95 Ext'd (LBA)
/dev/sda5            1531        4864    26780323+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ea832cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       26344   211608148+   5  Extended
/dev/sdb5               1         653     5245159+  83  Linux
/dev/sdb6            3265       17216   112069408+  83  Linux
/dev/sdb7           17217       17347     1052226   82  Linux swap / Solaris
/dev/sdb8           17348       17833     3903763+  83  Linux
/dev/sdb9             654        3264    20972826   83  Linux
/dev/sdb10          17834       19049     9767488+  83  Linux
/dev/sdb11          19050       21481    19535008+  83  Linux
/dev/sdb12          21482       26344    39062016   83  Linux

Partition table entries are not in disk order
```

And this is my menu.lst (minus about 120 lines of commentary and default options at the beginning):
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=f08c61ac-5e32-4a45-9acf-fbbd21c1b112 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=f08c61ac-5e32-4a45-9acf-fbbd21c1b112 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

It seems a bit strange that even though Windows is on my first hard disk and Linux on the second, it says (hd1,0) for XP and (hd0,4) for Ubuntu in my menu.lst, but that was the only way I could get Ubuntu to boot at all...
Any ideas what is going on?

---

### Post by SkonesMickLoud on 2008-07-12
Does setting the XP 'root' line to (hd0,0) allow it to boot?

---

### Post by GandalfNK on 2008-07-12
No, that causes an "Error 12: Invalid device requested".

---

### Post by confused57 on 2008-07-12
You might try map lines in your Windows entry:
```
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

---

### Post by GandalfNK on 2008-07-12
Woohoo! :D Works like a charm.
Thank you!

---

### Post by confused57 on 2008-07-12
> **GandalfNK said:**
> Woohoo! :D Works like a charm.
Thank you!
Glad to help & that it worked...

---

