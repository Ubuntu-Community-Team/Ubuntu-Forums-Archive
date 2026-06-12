---
title: "Partitioning problem / reassingning partitions"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by Ijan on 2008-07-20
Hello everybody, 

I'm a newbie to Linux and have just arrived here, so I hope chose the right forum for my problem.

I've run Ubuntu 8.04 in a dual boot setup with Windows XP SP2. Working under Windows today **I temprarily needed to create an extra primary partition**, wich I did from the M$-managment console. (On install I used gparted.) After it had created the new NTFS partition it appeared to me, my logical partition for the linux-swap was now labeled as unasigned space.

When I booted into a gparted live system afterwards to clean up I found that gparted didn't recognize any partitions on my harddisk any more.

Luckyly my ubuntu booted successfully, though it displayed some protesting boot messages. But: apparently my swap-partition doesn't seem to be used any more and the fat32 partition I keep my shared mozilla profiles on wasn't mounted on startup. 

After I changed the partition# according to the extra primary partition I added it worked again, was this sufficent?

```

before: [COLOR="Red"]/dev/sda5[/COLOR] /media/NR3-DATA vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

after: [COLOR="Red"]/dev/sda6[/COLOR] /media/NR3-DATA vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

```

Apart from that I'm afraid I'll need some help getting my system in a consistant state again and to get rid of the error messages on startup.

First, how do I correctly reassign the other partitions (swap, /, /home)? And how do I get my hd to be correctly recognized by gparted again? Or is there a better way dealing with this?
 
Here's some information that is supposed to be helpful:

```

**$:mount**

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda5 on /home type ext3 (rw,relatime)
/dev/sda6 on /media/NR3-DATA type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
gvfs-fuse-daemon on /home/user1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user1)
/dev/sdb1 on /media/USB-STICK1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```

```

**$:fdisk -l**

omitting empty partition (5)
omitting empty partition (5)

Platte /dev/sda: 200.0 GByte, 200049647616 Byte
255 Köpfe, 63 Sektoren/Spuren, 24321 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x307a3079

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        6423    20876467+   7  HPFS/NTFS
/dev/sda3            6424        9483    24579450   83  Linux
/dev/sda4            9484       24321   119186235    5  Erweiterte
/dev/sda5            9803       11077    10241406   83  Linux
/dev/sda6           11078       24321   106382430    b  W95 FAT32

```

```

**$:blkid**

/dev/sda1: UUID="0C28BC5528BC400E" LABEL="XP System" TYPE="ntfs" 
/dev/sda3: UUID="8cb4c152-d70c-4b7c-9f07-64093d251396" TYPE="ext3" 
/dev/sda5: UUID="78f7b048-bfea-4da7-974c-cc2c4aeb6fa2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="NR3-DATA" UUID="47F7-9F42" TYPE="vfat" 
/dev/sda2: UUID="1038451A38450068" LABEL="NTFS-DATA" TYPE="ntfs" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="USB-STICK1" UUID="2479-7321" TYPE="vfat" 

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8cb4c152-d70c-4b7c-9f07-64093d251396 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=78f7b048-bfea-4da7-974c-cc2c4aeb6fa2 /home           ext3    relatime        0       2
# /dev/sda6
UUID=1b7d659e-8e94-451c-81f7-02680b9c997e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda6 /media/NR3-DATA vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

```

Help is much appreciated!
Ijan

---

