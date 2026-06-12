---
title: "Can't boot Dapper after kernel upgrade"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by Libertine on 2006-10-21
Hey everyone, I installed Dapper the other day and everything was working fine until I updated. Now when I try to boot, the bootloader hangs on "Mounting Filesystem" and then gives me a Busybox error about /dev/hda1 not existing on root.

I think it's important to say that I have two hard drives on my system: an IDE for Ubuntu and a SATA for Windows.

Here is the output of fdisk -l:

```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS
```

Can anyone help me with this? Thanks! :)

---

### Post by gn2 on 2006-10-21
> **Libertine said:**
> Hey everyone, I installed Dapper the other day and everything was working fine until I updated. Now when I try to boot, the bootloader hangs on "Mounting Filesystem" and then gives me a Busybox error about /dev/hda1 not existing on root.

I think it's important to say that I have two hard drives on my system: an IDE for Ubuntu and a SATA for Windows.

Here is the output of fdisk -l:

```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS
```

Can anyone help me with this? Thanks! :)

Perhaps this will help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

