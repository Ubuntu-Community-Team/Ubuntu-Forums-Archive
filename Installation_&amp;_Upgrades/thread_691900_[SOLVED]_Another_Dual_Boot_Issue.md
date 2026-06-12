---
title: "[SOLVED] Another Dual Boot Issue"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by dadsy on 2008-02-09
I'm hoping someone might be able to provide a few suggestions. I've spent a fair bit of time searching for some answers but haven't come up with my much. 

I've got a system with 2 IDE HDD's, 1 x 40gb for Ubuntu and possible another distro down the line, 1 x 80 gb as a storage disk, and  an 80 gb SATA for XP SP2. When ever I've tried to dual boot selecting XP in GRUB ends up with NTLDR missing. I know it's not missing as I can select the SATA HDD to boot from and it works.

I have a question and a favour to ask. The question is; after making changes to the menu.lst file, do I have to "update" GRUB or does it update on restart?

The favour is; can someone please have a look at my menu.lst and fdisk -l to see if there's something obviously wrong. 

I've tried the Hermanzone links and searched a heap of the dual boot problems but couldn't find a solution or one that i could understand. I'm brand new to all things linux and am very keen to keep using it.

My menu.lst
```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4c8debd5-3cbc-421a-a9d1-d277248dbe52 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4c8debd5-3cbc-421a-a9d1-d277248dbe52 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

And my fdisk -l
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3fe7396

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x930dd27a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17d217d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS

```

Here's my fstab for good measure.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4c8debd5-3cbc-421a-a9d1-d277248dbe52 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=de17a49c-30cf-4a15-9970-98f080afc714 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Any advice is appreciated. In the mean time, I'll keep looking.

Cheers.

---

### Post by logos34 on 2008-02-09
Try editing XP stanza thusly:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Home Edition
root		(hd[COLOR="Red"]1[/COLOR],0)
savedefault
makeactive
map		(hd0) (hd[COLOR="Red"]1[/COLOR])
map		(hd[COLOR="Red"]1[/COLOR]) (hd0)
chainloader	+1

In order for it to work you may also have to edit /boot/grub/device.map to make it match.

ADD: If you want to mount those ntfs partitions in linux[ take a look here]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971").

---

### Post by lha on 2008-02-09
> **dadsy said:**
> I have a question and a favour to ask. The question is; after making changes to the menu.lst file, do I have to "update" GRUB or does it update on restart?

Grub reads menu.lst on each boot; there's no need for "updating".

---

### Post by dadsy on 2008-02-09
Thanks guys.

Logos34: Worked like a charm. Cheers.

I now have a working dual boot. As one bloke said "Ive never been so blimmin happy to see the windows scroll bar."

---

