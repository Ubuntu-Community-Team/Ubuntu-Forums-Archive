---
title: "Grub/Ubuntu Live USB destroys Partitions"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by puerto.rico.rolf on 2010-01-03
hi!

i have a serious problem. i installed ubuntu 9.10 on a usb pen drive. i booted and it works fine but destroyed the linux partition on my hard drive. it had a windows/ubuntu dual boot but now the filesystem of the linux partition is "unknown". thus, grub gives error 17.

the same happend on a similar system after booting from usb pen drive!

parted shows **partitions** like this:

```

(parted) print                                                            
Model: ATA ST9120822AS (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  53.7GB  53.7GB  primary   ntfs            boot
 2      53.7GB  120GB   66.3GB  extended
 5      53.7GB  117GB   63.6GB  logical   [edit: FS MISSING!!!]
 6      117GB   120GB   2755MB  logical   linux-swap(v1)

```as you can see, partition number 5 hasn't a filesystem anymore.

the **grub** code i used for **booting** looked like this:

```

menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        set root=(hd0,1)
        linux   /boot/vmlinuz-2.6.31-16-generic root=/dev/sdb1 ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-16-generic
}

```the **fstab** was generated like this:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ffdefc9c-5ea6-4067-aa84-a38434d7b862 /               ext4    errors=remount-ro 0       1
# /stick was on /dev/sda3 during installation
UUID=77C4-50C2  /stick          vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
#UUID=e31e9517-c043-4f1d-9305-a0901c54128e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```any idea how this boot process could kill partitions!?

(recovery with parted or testdisk was not possible so far)

thank you!
björn

---

### Post by tachuela on 2010-01-03
Use Super Grub Disk and you will still be able to boot your internal drives. Partition 5 (logical) doesn't have a file system because it is enveloping your swap partition.

---

