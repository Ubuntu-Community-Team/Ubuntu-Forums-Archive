---
title: "Recovering from failed Ubuntu 14.10 upgrade"
date: 2014-10-25
forum: Installation &amp; Upgrades
---

### Post by centinela0 on 2014-10-25
This morning I attempted to upgrade from Ubuntu 14.04 to 14.10. The upgrade process proceeded as normal, until about 50% through package installation. Various packages began failing to install. Eventually, enough failed that it looked like the system was attempting to revert to some known-good state. However, it is in a state where it will not boot.

When I attempt to boot, I see the following errors.

mount: mounting/dev on/root/dev failed: No Such File or Directory
mount: mounting/sys on/root/sys failed: No Such File or Directory
mount: mounting/proc on/root/proc failed: No Such File or Directory
Target Filesystem doesn't have requested /sbin/init.
No init found. Try passing init=bootarg.

Searching around a bit, I thought it might be as simple as cleaning up the filesystem:

ubuntu@ubuntu:/media/ubuntu$ sudo fdisk -l

Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/loop1: 496 MiB, 520093696 bytes, 1015808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x86c69001

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1               63      80324      80262  39.2M de Dell Utility
/dev/sda2  *         81920   22900735   22818816  10.9G  7 HPFS/NTFS/exFAT
/dev/sda3         22900736  873856030  850955295 405.8G  7 HPFS/NTFS/exFAT
/dev/sda4        873857022 1953523711 1079666690 514.8G  5 Extended
/dev/sda5        873857024 1909759999 1035902976   494G 83 Linux
/dev/sda6       1909762048 1953523711   43761664  20.9G 82 Linux swap / Solaris

Disk /dev/sdf: 14.6 GiB, 15703474176 bytes, 30670848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdf1  *       32 30670847 30670816 14.6G  c W95 FAT32 (LBA)

ubuntu@ubuntu:/media/ubuntu$ sudo fsck /dev/sda5
fsck from util-linux 2.25.1
e2fsck 1.42.10 (18-May-2014)
/dev/sda5: clean, 319766/32374784 files, 10211321/129487872 blocks

However, it comes up as clean, and nothing is changed. I am dual booting Windows 7 and Ubuntu on this machine. 

I'm looking for some suggestions as to what to try next.

---

### Post by mikewhatever on 2014-10-25
You could try backing up important data (if any), and doing a clean install. You could also install, while not formatting the root partition - a sort of recovery, if you will.

---

### Post by centinela0 on 2014-10-26
I'd like to try installing without formatting the root partition.  However, if you could provide some explicit instructions, that would be  great. (I'm trying not to worsen the mess I've made for myself). I've  been using Ubuntu 14.10 on a USB stick for recovery.

---

