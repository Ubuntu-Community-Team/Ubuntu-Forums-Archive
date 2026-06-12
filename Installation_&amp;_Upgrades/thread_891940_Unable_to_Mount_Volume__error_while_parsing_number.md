---
title: "Unable to Mount Volume / error while parsing numbers"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by Jasonhdavis on 2008-08-16
Hello

I am duel booting XP and Ubuntu (Hardy) with several other drives for different media. After installing with advanced options to place GRUB on the Ubuntu partition I get the error Unable to Mount Volume.

I believe this problem is caused because GRUB is calling hd1,4 the root instead of dev/sdb5. When I attempted changing this in the GRUB command line, it told me "Error while parsing numbers"

Here's fdisk -l
```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54ed5163

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        7297    58605120    f  W95 Ext'd (LBA)
/dev/sda5               2        7297    58605088+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32833544

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10703    85971816    7  HPFS/NTFS
/dev/sdb2           10704       30401   158224185    5  Extended
/dev/sdb5   *       10706       14621    31455238+  83  Linux
/dev/sdb6           14622       17232    20972826    7  HPFS/NTFS
/dev/sdb7           17233       30401   105779961    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000f116

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         393     3156741    7  HPFS/NTFS
/dev/sdc2             394       10130    78212452+   7  HPFS/NTFS
/dev/sdc3           10131       30756   165678345    7  HPFS/NTFS
/dev/sdc4           31011       91201   483484207+   f  W95 Ext'd (LBA)
/dev/sdc5           31153       91201   482343561    7  HPFS/NTFS
/dev/sdc6           31012       31152     1132551   82  Linux swap / Solaris

Partition table entries are not in disk order

```

and the important(?) part of menu.lst
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5ca5766d-0a24-425f-96cc-9e4c648d297e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5ca5766d-0a24-425f-96cc-9e4c648d297e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

This is my first Ubuntu install. I hope someone can help me get it working!

Thanks!
Jason

---

### Post by jualin on 2008-08-16
Grub doesn't use dev/sdb to identify the hard drives or partition it uses hdx,x, so you should change it back.

---

### Post by Jasonhdavis on 2008-08-16
> **jualin said:**
> Grub doesn't use dev/sdb to identify the hard drives or partition it uses hdx,x, so you should change it back.

I guess that explains the "error while parsing numbers" error?

What about the Unable to Mount Volume?

---

