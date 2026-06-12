---
title: "Trying to get Grub2 to see my Gentoo kernel"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by davidogg on 2010-07-16
[B]I have several Linux distro's spread out on these 2 drives. sdb is the primary slave, sda is the secondary master. (they got jumpered goofy years ago, and I havent dared touch it, but it seems to work, so...)

I installed Gentoo on sda7, and when I run update-grub from Ubuntu, it sees my gentoo kernel and appears as though it's added it, however when I reboot it doesn't show in the menu. Grub is on sdb1, I believe

This is my rats nest of partitions;[/B]

david@david-lucid:~$ sudo fdisk -l
[sudo] password for david: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90c090c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3826       60801   457659658    f  W95 Ext'd (LBA)
/dev/sda2               1        3825    30724281    7  HPFS/NTFS
/dev/sda5           31744       60801   233408385    7  HPFS/NTFS
/dev/sda6            3826        7678    30949159+  83  Linux
/dev/sda7            7679       11047    27061461   83  Linux
/dev/sda8           11048       14234    25599546   83  Linux
/dev/sda9           14235       14549     2530206   82  Linux swap / Solaris
/dev/sda10          14550       31743   138110773+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160029999616 bytes
255 heads, 63 sectors/track, 19455 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xab42ab42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13        5074    40653481    7  HPFS/NTFS
/dev/sdb3            5075       18822   110430810   83  Linux
/dev/sdb4           18823       19455     5084572+  82  Linux swap / Solaris

Disk /dev/sdc: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9d0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1021     3924693    c  W95 FAT32 (LBA)
david@david-lucid:~$ 
 
**This is the output from update-grub;**

david@david-lucid:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Gentoo Base System release 1.12.13 on /dev/sda7
Found Windows 7 (loader) on /dev/sdb1
Found Ubuntu maverick (development branch) (10.10) on /dev/sdb3
done
david@david-lucid:~$ 
[B]
Am I doing it wrong?
[/B]

---

### Post by lechien73 on 2010-07-16
I had read about this before, where os-prober (or linux-boot-prober - depending on which one you're using) detects another operating system, but then fails to add it to Grub.

Others have said that os-prober seems to be better than linux-boot-prober at detecting other operating systems. So you could check which prober you're using:

```
which os-prober
which linux-boot-prober

```

If os-prober doesn't return a path (/usr/bin/os-prober), then you can install and use it by typing:

```
sudo apt-get install libdebian-installer4
sudo os-prober
sudo update-grub

```

If things are still the same when you reboot, then another solution would be to include the Gentoo installation in the /etc/grub.d/40_custom file. You can do this by adding the following lines after the comment:

```
echo "Adding Gentoo Base System" >&2
cat << EOF
menuentry "Gentoo Base System custom" {
        set root=(hd0,7)
        linux /boot/gentoo root=/dev/sda7 ro
}
EOF
```

Then make the file executable:

```
sudo chmod +x /etc/grub.d/40_custom
```

Finally:

```
sudo update-grub
```

And reboot one more time :)

---

### Post by ogredeschnique on 2010-07-17
I'm receiving a "file missing" error after adding my Gentoo info /etc/grub.d/40_custom. 
I guess it's time to get familiar with the grub2 command line at boot. 

Seems like this should work properly. 

```
menuentry "Gentoo Linux" {
set root=(hd0,2)
linux /boot/gentoo-2.6.34-r1 root="/dev/sda3"
}
EOF
```

[Another edit]
Ah ha. I just noticed that grub2 numbers devices differently. The first disk is still zero, but the third partition is not the third from zero. That is so weird.

---

