---
title: "Flashing Ubuntu server onto and Android ARM64 device"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2016-08-11
Slightly off topic but :

I've picked up one of those android "TV boxes" it's running a Octa-Core ARM64 chip Rockchip 3386 (KR3386) with Android 5.1 (**[https://www.amazon.co.uk/gp/product/B01G6MJM7C](https://www.amazon.co.uk/gp/product/B01G6MJM7C))**

Just wondering if anyone has tried flashing the ARM64 version of Ubuntu on to it?

Or what partitions would I need to flash to get it running?

Partitions:
```

major minor  #blocks  name

 254        0     520912 zram0
 179        0   15388672 mmcblk0
 179        1       4096 mmcblk0p1
 179        2       4096 mmcblk0p2
 179        3       4096 mmcblk0p3
 179        4      16384 mmcblk0p4
 179        5      16384 mmcblk0p5
 179        6      32768 mmcblk0p6
 179        7      32768 mmcblk0p7
 179        8     114688 mmcblk0p8
 179        9     131072 mmcblk0p9
 179       10       4096 mmcblk0p10
 179       11    1572864 mmcblk0p11
 179       12      16384 mmcblk0p12
 179       13       4096 mmcblk0p13
 179       14      65536 mmcblk0p14
 179       15   13361152 mmcblk0p15

```
Partition Mappings : 
```

lrwxrwxrwx root     root              2011-01-01 12:00 backup -> /dev/block/mmcblk0p8
lrwxrwxrwx root     root              2011-01-01 12:00 baseparamer -> /dev/block/mmcblk0p13
lrwxrwxrwx root     root              2011-01-01 12:00 boot -> /dev/block/mmcblk0p6
lrwxrwxrwx root     root              2011-01-01 12:00 cache -> /dev/block/mmcblk0p9
lrwxrwxrwx root     root              2011-01-01 12:00 kernel -> /dev/block/mmcblk0p5
lrwxrwxrwx root     root              2011-01-01 12:00 kpanic -> /dev/block/mmcblk0p10
lrwxrwxrwx root     root              2011-01-01 12:00 metadata -> /dev/block/mmcblk0p12
lrwxrwxrwx root     root              2011-01-01 12:00 misc -> /dev/block/mmcblk0p3
lrwxrwxrwx root     root              2011-01-01 12:00 radical_update -> /dev/block/mmcblk0p14
lrwxrwxrwx root     root              2011-01-01 12:00 recovery -> /dev/block/mmcblk0p7
lrwxrwxrwx root     root              2011-01-01 12:00 resource -> /dev/block/mmcblk0p4
lrwxrwxrwx root     root              2011-01-01 12:00 system -> /dev/block/mmcblk0p11
lrwxrwxrwx root     root              2011-01-01 12:00 trust -> /dev/block/mmcblk0p2
lrwxrwxrwx root     root              2011-01-01 12:00 uboot -> /dev/block/mmcblk0p1
lrwxrwxrwx root     root              2011-01-01 12:00 userdata -> /dev/block/mmcblk0p15

```

It's working OK with Android, but it's limited to the APK's available!. I think it could be a nice little Linux server to take the load off my old linux box.
Their are tools out there to backup and flash the Rockchip CPU's but I can't get them to see my device for some reason. 
So at the moment I'm stuck trying to manually pull the partition images form the device before i even attempt flashing it with another OS!

Any info or help will be welcomed ;)

*update*
Just wondering if an Ubuntu Touch install would be easier? Can that act like a generic server (without the telephone bits??)

---

