---
title: "Multiple disk grub problem"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by gwon on 2007-07-03
I had previously had a different linux distro installed (zenwalk), which also had a boot loader of some sort set up (I think it's lilo).

Anyway, I just did an install of ubuntu, using the option in the partitioner for it to use the entire disk (/dev/hda - the second one from below).

Everything went fine till the reboot, where I get the old zenwalk lilo screen. I'd assumed that the ubuntu installer would have wiped my old boot loader away, but apparently didn't.

What I'm looking for is for someone to talk me through getting a new grub installed onto the mbr of my first disk.

Luckily enough, the lilo boot loader still works in so much as it gets me to windows, so it's not as big a problem as it could have been, I'd just like to get to my new ubuntu installation :(

Disk details:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS  (WINDOWS)
/dev/sda2            6375       23716   139299615    7  HPFS/NTFS(FILES)

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9587    77007546   83  Linux                           (root)
/dev/hda2            9588        9964     3028252+   5  Extended
/dev/hda5            9588        9964     3028221   82  Linux swap / Solaris

```

---

### Post by logos34 on 2007-07-03
What happens when you set the BIOS to boot first from the other drive?

---

### Post by gwon on 2007-07-03
Brilliant. Don't know why that didn't occur to me.

Thanks for your help.

---

