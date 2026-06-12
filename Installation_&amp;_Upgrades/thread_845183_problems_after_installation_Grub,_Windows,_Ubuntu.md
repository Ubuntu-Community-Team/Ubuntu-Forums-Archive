---
title: "problems after installation: Grub, Windows, Ubuntu"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by Puffin-ww on 2008-06-30
Dear folks

I've just installed Ubuntu 8.04. Installation seems to have run OK.
I've put Ubuntu on a new, third harddisk. Before installing, I prepared three partitions there, in Windows (XP), with PartitionMagic, for /, swap and home.
During the installation procedure / Advanced, I chose to install the boot loader into /dev/sdc1, i.e. the root-partition to be.

(According to PartitionMagic, the root-partition is now filled with about 2.5 GB. Is that OK?)

Now the situation is like this:
With the standard BIOS harddisk boot sequence 1,2,3 Windows starts, but GRUB is nowhere to be seen.
With the sequence 3,1,2 GRUB starts, but when I choose Ubuntu, I get error 17 ("Cannot mount selected partition"); and when I choose Windows, nothing happens, i.e. Grub shows its options again after a while.

So, the whole thing is not running perfectly yet ...

What can I do to have Grub always appear (also when I boot from HD1), and what can I do in order to get both Ubuntu and Windows to run from Grub?

(If necessary, it wouldn't be a problem to install Ubuntu again.)

Thanks

Puffin-ww

---

### Post by VMC on 2008-06-30
Leave your BIOS default. In other words you don't have to manipulate your BIOS to boot ubuntu. Windows is installed first. So now you installed ubuntu on a third hard drive. Now we need to see everything.

Open up a Terminal from here "Applications-Accessories-Terminal", and type this:

```
sudo fdisk -l
```
[lower-case "L"]
copy and paste the output.

---

### Post by Puffin-ww on 2008-06-30
Here you are:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d578d57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1146     9205213+   7  HPFS/NTFS
/dev/sda2            1147        7521    51207187+   f  W95 Ext'd (LBA)
/dev/sda5            1147        1401     2048256    7  HPFS/NTFS
/dev/sda6            1402        2166     6144831    7  HPFS/NTFS
/dev/sda7            2167        3568    11261533+   7  HPFS/NTFS
/dev/sda8            3569        6756    25607578+   7  HPFS/NTFS
/dev/sda9            6757        7521     6144831    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84506fab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1146     9205213+   7  HPFS/NTFS
/dev/sdb2            1147        9306    65545200    f  W95 Ext'd (LBA)
/dev/sdb5            1147        1401     2048256    7  HPFS/NTFS
/dev/sdb6            1402        2993    12787708+   7  HPFS/NTFS
/dev/sdb7            2994        3312     2562336    7  HPFS/NTFS
/dev/sdb8            3313        3950     5124703+   7  HPFS/NTFS
/dev/sdb9            3951        7138    25607578+   7  HPFS/NTFS
/dev/sdb10           7139        7903     6144831    7  HPFS/NTFS
/dev/sdb11           7904        8668     6144831    7  HPFS/NTFS
/dev/sdb12           8669        9306     5124703+   b  W95 FAT32

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd2baf81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1913    15366141   83  Linux
/dev/sdc2            1914        3450    12345952+   f  W95 Ext'd (LBA)
/dev/sdc5            1914        2175     2104483+  82  Linux swap / Solaris
/dev/sdc6            2176        3450    10241406   83  Linux

---

### Post by dstew on 2008-06-30
> During the installation procedure / Advanced, I chose to install the boot loader into /dev/sdc1, i.e. the root-partition to be.This is part of the problem. If you wanted grub to be the main boot loader, and use it to boot Windows, you should have installed it in the MBR of the first disk, and not in the Ubuntu partition.

You can re-install grub using the Live CD. Open a terminal, and start the grub shell with the command```
sudo grub
``` That should get you the grub command line, with a **grub>** prompt. At the grub prompt, enter```
find /boot/grub/stage2
```Based on your fdisk output, it will probably give you (hd2,0) as the answer. Whatever it gives you, use as the argument of a root statement:```
root (hd2,0)
```Then, install the boot loader into the MBR of the first hard drive, and quit the grub shell:```
setup (hd0)
quit
```Then, shut down the Live CD system, remove the CD and reboot. Hopefully it will at least get to the grub menu. If the menu items don't work, we can fix those too.

---

