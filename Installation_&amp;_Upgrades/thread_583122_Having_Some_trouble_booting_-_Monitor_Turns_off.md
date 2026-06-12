---
title: "Having Some trouble booting - Monitor Turns off"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by MarksWeb on 2007-10-20
Hey :)

With the release of 7.1 i've finally decided to switch back to Ubuntu :)

I've also got XP installed and a lot of NTFS paritions which i've got stuff on from using XP...

Now i've installed Gutsy and i'm having big problems with GRUB.
When i try to launch gutsy from grub it loads the kernel then the monitor goes to powersaver. I fixed this exact same issue with the Live CD by simply booting with noquiet and nosplash - but i've tried to edit the boot command in GRUB the same way and its still just shutting down my monitor after i launch gutsy!

further more grub can't see my XP install - just an old Vista Launcher (i uninstalled vista and put gutsy on it's partition space). When i tried to change my HDD boot priority to get back to XP hal.dll has corrupted and i can't mount the NTFS disk thats got XP on it to copy a working version of hal.dll

Could somebody give me some assistance with these issues please :)

and incase it helps...my hardware is...

A64 3500
2gb
ATi x850XT

(i'm currently running off the live cd cose my installed OS's wont work)

---

### Post by MarksWeb on 2007-10-20
My disks look a bit like -

```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc84e479

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3843    30868866   83  Linux
/dev/hda2            8542       19929    91474110    f  W95 Ext'd (LBA)
/dev/hda3            3844        8250    35399227+  83  Linux
/dev/hda4            8251        8541     2337457+  82  Linux swap / Solaris
/dev/hda5            8542       11091    20482843+   7  HPFS/NTFS
/dev/hda6           11092       14915    30716248+   7  HPFS/NTFS
/dev/hda7           14916       17465    20482843+   7  HPFS/NTFS
/dev/hda8           17466       19929    19792048+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf076a47

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1026     8241313+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xa752f630

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      101587    51199816+   7  HPFS/NTFS
/dev/sda2          101588      484520   192998232    f  W95 Ext'd (LBA)
/dev/sda5          101588      142222    20480008+   7  HPFS/NTFS
/dev/sda6          142223      203174    30719776+   7  HPFS/NTFS
/dev/sda7          203175      281345    39398152+   7  HPFS/NTFS
/dev/sda8          281346      382932    51199816+   7  HPFS/NTFS
/dev/sda9          382933      433726    25600144+   7  HPFS/NTFS
/dev/sda10         433727      484520    25600144+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9d330fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```

XP is sat on /hdb1

hopefully that helps? :confused:

---

