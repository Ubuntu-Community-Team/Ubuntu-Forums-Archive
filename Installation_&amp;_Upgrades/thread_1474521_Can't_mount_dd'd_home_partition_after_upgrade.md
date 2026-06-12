---
title: "Can't mount dd'd home partition after upgrade"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by bob_hilton on 2010-05-06
When i had 9.10 installed i had /home and / on separate partitions but this time, i wanted them both within the same.

I dd'd my old home partion to an external drive, wiped the old partitions and installed lucid but now i cant mount the drive.

im trying to use:

```
sudo mount -o loop -t auto /mnt/storage/home.img /mnt/oldhome/
```

but i get an error of wrong fs type, bad option or bad superblock.

fdisk -l shows:

```
Disk /mnt/storage/home.img: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /mnt/storage/home.img doesn't contain a valid partition table

```

But in nautilus it shows it as the full 23.6 gb its supposed to be?

---

### Post by dino99 on 2010-05-06
need to run fsck: will run it on next boot: sudo shutdown -F -r now

the easiest and secured way to deal with your devices and partitions is to install MountManager and tweak it as you need

---

