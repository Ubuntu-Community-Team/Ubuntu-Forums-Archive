---
title: "uninstall problem"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by siglio21 on 2008-07-22
Oh gawd...how should I start.

A few hours ago, I decided to uninstall Ubuntu. I (thought I had) changed my MBR correctly, deleted my Ubuntu partition and rebooted.

Grub Error 17

OK. Live CD. ms-sys -p -m -f /dev/sda

Reboot.

Partition table corrupted.

Live CD

Test Disk. Fixed NTFS boot.

Reboot.

Blinking cursor.

Now I'm stuck. I don't have a XP install disc with me or any other boot disc.

Please help me.

Note: I tried reinstalling Ubuntu before I ran ms-sys. That didn't go so well (didn't install it at all), but I got past the partitioning which mean things might suck for me now (I *might* have accidentally wiped
that partition, although I can't be sure.)

---

### Post by Pumalite on 2008-07-22
Boot Live CD
Post:
sudo fdisk -lu

---

### Post by siglio21 on 2008-07-22
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     8514450   412484939   201985245    7  HPFS/NTFS
/dev/sda2              63     8514449     4257193+   b  W95 FAT32
/dev/sda3       485179065   488392064     1606500    f  W95 Ext'd (LBA)
/dev/sda5       485179128   488392064     1606468+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

