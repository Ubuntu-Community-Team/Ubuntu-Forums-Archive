---
title: "hard drives get fsck'ed on every boot [ubuntu studio]"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by liniaal on 2007-11-27
hi people,

the problem is this: lately i deleted my old ubuntu partition and replaced it with ubuntu studio gutsy, i'm really very happy with it. since i have my home dir on a different partition, all my settings saved and are intact. it's very little work to get everything back to work as it did before (lots of apt-gets of course).

only one thing is weird: my mounts now get checked every time i boot the pc, while in the past it was only once in a while (26 times mounted without being checked, or something like that i remember :)). has this to do with grub not being the MBR but on a /dev/sda2, or with my /etc/fstab options, or what could this be?

is this default behavior in ubuntu studio? if it was only the root partition that was checked so much, it would not be a very big problem for me, but now it really slows down boot with about 4 minutes :(.

[SIZE="1"]luckily it was very easy for me to install the gdm theme from ubuntu studio feisty since i have that still installed on my laptop :D.[/SIZE]

---

### Post by prodezigner on 2007-11-27
This isn't going to help, but I just want to point out that everytime someone says 'fsck'ed' I think fxxked. LOL.

---

### Post by liniaal on 2007-11-27
> **prodezigner said:**
> This isn't going to help, but I just want to point out that everytime someone says 'fsck'ed' I think fxxked. LOL.

hehehe me too, i like to think it's called fsck just for that reason. or because windows-like systems are known for 'fsck'ing' up your filesystems during the File System Check ;p. but anyway, let's get to business. here is my /etc/fstab;

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=88175e2e-2ab0-446e-8b9f-14ffc68abdd6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=7e05a1c3-a5e5-4802-a6b3-0253d18977b0 /home           ext3    defaults        0       2
# /dev/sda7
UUID=458C-6A7C  /mnt/data       vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=458C-6A77  /mnt/games      vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=4623-37DE  /mnt/media      vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=e44234a3-f9a6-41ca-985f-5566ab24c7a6 /mnt/zenwalk    ext3    defaults        0       2

```

---

### Post by reikoshea on 2007-11-27
> **liniaal said:**
> hehehe me too, i like to think it's called fsck just for that reason. or because windows-like systems are known for 'fsck'ing' up your filesystems during the File System Check ;p. but anyway, let's get to business. here is my /etc/fstab;

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=88175e2e-2ab0-446e-8b9f-14ffc68abdd6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=7e05a1c3-a5e5-4802-a6b3-0253d18977b0 /home           ext3    defaults        0       2
# /dev/sda7
UUID=458C-6A7C  /mnt/data       vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=458C-6A77  /mnt/games      vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=4623-37DE  /mnt/media      vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=e44234a3-f9a6-41ca-985f-5566ab24c7a6 /mnt/zenwalk    ext3    defaults        0       2

```

This happens all the time with vfat partitions.  The way to disable is to set the pass option to 0 in your fstab.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=88175e2e-2ab0-446e-8b9f-14ffc68abdd6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=7e05a1c3-a5e5-4802-a6b3-0253d18977b0 /home           ext3    defaults        0       2
# /dev/sda7
UUID=458C-6A7C  /mnt/data       vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda6
UUID=458C-6A77  /mnt/games      vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sdc1
UUID=4623-37DE  /mnt/media      vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda4
UUID=e44234a3-f9a6-41ca-985f-5566ab24c7a6 /mnt/zenwalk    ext3    defaults        0       2

```

That should take care of it.

---

