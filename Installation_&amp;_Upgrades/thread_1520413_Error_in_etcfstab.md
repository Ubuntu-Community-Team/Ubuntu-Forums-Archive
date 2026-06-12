---
title: "Error in /etc/fstab"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by hariks0 on 2010-06-29
Recently I upgraded to 10.4 by complete reinstalltion. When I boot to Ubuntu there is a message displayed that reads *"Keys: Wait to continue; or S to skip or M to manually mount"* The wordings are not exact but you get the idea. I have to press 'S' twice to complete the bootup which is stuck at this message. The partitions are not mounted properly as I expected. Earlier the partitions were listed in Nautilus as DriveC, DriveD etc in the side pane. Now they are listed under file system only. The contents of my /etc/fstab is :-

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=a66652d0-a90e-4d97-9a21-387853831cea /               ext4    errors=remount-ro 0       1
# /DriveC was on /dev/sda2 during installation
UUID=D020576520575198 /DriveC         ntfs    defaults,umask=007,gid=46 0       0
# /DriveD was on /dev/sda5 during installation
UUID=4024497624497048 /DriveD         ntfs    defaults,umask=007,gid=46 0       0
# /DriveE was on /dev/sda6 during installation
UUID=46400AAF400AA631 /DriveE         ntfs    defaults,umask=007,gid=46 0       0
# /DriveF was on /dev/sda7 during installation
UUID=03AB01E67E33EB5F /DriveF         ntfs    defaults,umask=007,gid=46 0       0
# /DriveG was on /dev/sda8 during installation
UUID=8693029d-691a-45f9-9f1c-bdf3b374fa12 /DriveG         ext4    defaults        0       2
# /DriveH was on /dev/sda9 during installation
UUID=f146e4b8-76b5-45be-b3fc-8483960c11c6 /DriveH         ext4    defaults        0       2
# /VHD was on /dev/sda13 during installation
UUID=6a1d65d8-0234-47a1-9497-a0884f55eaa7 /VHD            ext4    defaults        0       2
# /home was on /dev/sda12 during installation
UUID=ac0ffb9f-e573-4d96-85cb-0cddf15d002e /home           ext4    defaults        0       2
/dev/sda10      none            swap    sw              0       0
```

The output of fdisk is :-

```
hariharasuthan@Indira:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4be646c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6374    51094727    7  HPFS/NTFS
/dev/sda3            6375       91208   681422638+   f  W95 Ext'd (LBA)
/dev/sda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sda6           12749       16572    30716248+   7  HPFS/NTFS
/dev/sda7           16573       31263   118000000    7  HPFS/NTFS
/dev/sda8           31263       43428    97717248    7  HPFS/NTFS
/dev/sda9           43428       60814   139646976    7  HPFS/NTFS
/dev/sda10          60814       61421     4881408   82  Linux swap / Solaris
/dev/sda11          61422       64461    24413184   83  Linux
/dev/sda12          64461       72971    68358144   83  Linux
/dev/sda13          72971       91208   146484224   83  Linux

Disk /dev/sdb: 1025 MB, 1025506304 bytes
33 heads, 63 sectors/track, 963 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x89008558

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         964     1001455    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(225, 32, 63) logical=(963, 13, 46)
hariharasuthan@Indira:~$ 

```

What could be the problem? Should I try reinstalling?

Any help will be highly appreciated.

---

### Post by darkod on 2010-06-29
```
# /DriveG was on /dev/sda8 during installation
UUID=[COLOR=Red]8693029d-691a-45f9-9f1c-bdf3b374fa12[/COLOR] /DriveG [COLOR=Red]        ext4[/COLOR]    defaults        0       2
# /DriveH was on /dev/sda9 during installation
UUID=[COLOR=Red]f146e4b8-76b5-45be-b3fc-8483960c11c6[/COLOR] /DriveH         [COLOR=Red]ext4[/COLOR]    defaults        0       2

/dev/sda8           31263       43428    97717248    7  [COLOR=Red]HPFS/NTFS[/COLOR]
/dev/sda9           43428       60814   139646976    7  [COLOR=Red]HPFS/NTFS[/COLOR]
```sda8 and sda9 are specified as ext4 in fstab, and their UUIDs have ext4 type values, but fdisk says they are now ntfs.

I guess that's why after skipping to mount these two partitions, it continues working fine. You have changed something after the original install. You should also check the filesystem type and the UUID for every mount point in fstab, not just these two. You can check all the UUIDs with:

sudo blkid

Depending on the UUID and partition type, adjust the fstab but be very careful when editing fstab, it can mess up booting ubuntu if you delete/add wrong things.

---

### Post by CharlesA on 2010-06-29
Just remember you can always run this:

```
sudo mount -a
```

to mount all entries in fstab. It'll spit out errors if there are any, so you won't be stuck with an unbootable system if there is a mistake.

---

### Post by hariks0 on 2010-06-29
> **darkod said:**
> ```
# /DriveG was on /dev/sda8 during installation
UUID=[COLOR=Red]8693029d-691a-45f9-9f1c-bdf3b374fa12[/COLOR] /DriveG [COLOR=Red]        ext4[/COLOR]    defaults        0       2
# /DriveH was on /dev/sda9 during installation
UUID=[COLOR=Red]f146e4b8-76b5-45be-b3fc-8483960c11c6[/COLOR] /DriveH         [COLOR=Red]ext4[/COLOR]    defaults        0       2

/dev/sda8           31263       43428    97717248    7  [COLOR=Red]HPFS/NTFS[/COLOR]
/dev/sda9           43428       60814   139646976    7  [COLOR=Red]HPFS/NTFS[/COLOR]
```sda8 and sda9 are specified as ext4 in fstab, and their UUIDs have ext4 type values, but fdisk says they are now ntfs.

I guess that's why after skipping to mount these two partitions, it continues working fine. **You have changed something after the original install.** You should also check the filesystem type and the UUID for every mount point in fstab, not just these two. You can check all the UUIDs with:

sudo blkid

Depending on the UUID and partition type, adjust the fstab but be very careful when editing fstab, it can mess up booting ubuntu if you delete/add wrong things.

You are absolutely right ! I had formatted these partitions as NTFS using GParted after installtion. They are now available in Windows.

So, as per your reply, will changing the 'ext4' in fstab to 'HPFS/NTFS' will do the trick? Can you confirm that is what you mean?

Thank you so much for assistance.

---

### Post by oldfred on 2010-06-30
I have defaults on my NTFS mount in fstab. But you can also use the same settings (defaults,umask=007,gid=46) as you have on your other NTFS also. 

gksudo gedit /etc/fstab

or if from liveCD:
sudo mkdir /mnt/sda11
sudo mount /dev/sda11 /mnt/sda11
gksudo gedit /mnt/sda11/etc/fstab

---

### Post by hariks0 on 2010-07-04
I changed the entries in /etc/fstab as follows :-
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=a66652d0-a90e-4d97-9a21-387853831cea /               ext4    errors=remount-ro 0       1
# /DriveC was on /dev/sda2 during installation
UUID=D020576520575198 /DriveC         ntfs    defaults,umask=007,gid=46 0       0
# /DriveD was on /dev/sda5 during installation
UUID=4024497624497048 /DriveD         ntfs    defaults,umask=007,gid=46 0       0
# /DriveE was on /dev/sda6 during installation
UUID=46400AAF400AA631 /DriveE         ntfs    defaults,umask=007,gid=46 0       0
# /DriveF was on /dev/sda7 during installation
UUID=03AB01E67E33EB5F /DriveF         ntfs    defaults,umask=007,gid=46 0       0
# /DriveG was on /dev/sda8 during installation
UUID=8693029d-691a-45f9-9f1c-bdf3b374fa12 /DriveG         auto    defaults,umask=007,gid=46        0       0
# /DriveH was on /dev/sda9 during installation
UUID=f146e4b8-76b5-45be-b3fc-8483960c11c6 /DriveH         auto    defaults,umask=007,gid=46        0       0
# /VHD was on /dev/sda13 during installation
UUID=6a1d65d8-0234-47a1-9497-a0884f55eaa7 /VHD            ext4    defaults        0       2
# /home was on /dev/sda12 during installation
UUID=ac0ffb9f-e573-4d96-85cb-0cddf15d002e /home           ext4    defaults        0       2
/dev/sda10      none            swap    sw              0       0
```

But the same message appears still.

The other commands gave the following replies:-
```
hariharasuthan@Indira:~$ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="D0B04EA5B04E91C0" TYPE="ntfs" 
/dev/sda2: UUID="D020576520575198" TYPE="ntfs" 
/dev/sda5: LABEL="DDrive" UUID="4024497624497048" TYPE="ntfs" 
/dev/sda6: LABEL="EDrive" UUID="46400AAF400AA631" TYPE="ntfs" 
/dev/sda7: LABEL="MM" UUID="03AB01E67E33EB5F" TYPE="ntfs" 
/dev/sda8: LABEL="ISO" UUID="3B87373743B2E5BD" TYPE="ntfs" 
/dev/sda9: LABEL="VHD" UUID="174AC7022D706F8D" TYPE="ntfs" 
/dev/sda10: UUID="e01f4747-b327-4a5e-8983-303a54ddf7c8" TYPE="swap" 
/dev/sda11: UUID="a66652d0-a90e-4d97-9a21-387853831cea" TYPE="ext4" 
/dev/sda12: UUID="ac0ffb9f-e573-4d96-85cb-0cddf15d002e" TYPE="ext4" 
/dev/sda13: UUID="6a1d65d8-0234-47a1-9497-a0884f55eaa7" TYPE="ext4" 
/dev/ramzswap0: TYPE="swap" 
hariharasuthan@Indira:~$
```

```
hariharasuthan@Indira:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4be646c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6374    51094727    7  HPFS/NTFS
/dev/sda3            6375       91208   681422638+   f  W95 Ext'd (LBA)
/dev/sda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sda6           12749       16572    30716248+   7  HPFS/NTFS
/dev/sda7           16573       31263   118000000    7  HPFS/NTFS
/dev/sda8           31263       43428    97717248    7  HPFS/NTFS
/dev/sda9           43428       60814   139646976    7  HPFS/NTFS
/dev/sda10          60814       61421     4881408   82  Linux swap / Solaris
/dev/sda11          61422       64461    24413184   83  Linux
/dev/sda12          64461       72971    68358144   83  Linux
/dev/sda13          72971       91208   146484224   83  Linux

```

```
hariharasuthan@Indira:~$ sudo mount -a
mount: special device UUID=8693029d-691a-45f9-9f1c-bdf3b374fa12 does not exist
mount: special device UUID=f146e4b8-76b5-45be-b3fc-8483960c11c6 does not exist

```

Is it saying that the UUID has been changed on reformatting and I have to change the UUID in fstab? Is there any other way to correct this than complete reinstall?

---

### Post by Morbius1 on 2010-07-04
From fstab:
> # /DriveG was on /dev/sda8 during installation
[COLOR=Blue]UUID=8693029d-691a-45f9-9f1c-bdf3b374fa12[/COLOR] /DriveG         auto    defaults,umask=007,gid=46        0       0
# /DriveH was on /dev/sda9 during installation
[COLOR=Sienna]UUID=f146e4b8-76b5-45be-b3fc-8483960c11c6[/COLOR] /DriveH         auto    defaults,umask=007,gid=46        0       0
From blkid:
> /dev/sda8: LABEL="ISO" [COLOR=Blue]UUID="3B87373743B2E5BD[/COLOR]" TYPE="ntfs" 
/dev/sda9: LABEL="VHD" [COLOR=Sienna]UUID="174AC7022D706F8D" [/COLOR]TYPE="ntfs"So your fstab should be:
> [COLOR=Blue]UUID=[/COLOR][COLOR=Blue]3B87373743B2E5BD[/COLOR]  /DriveG         auto    defaults,umask=007,gid=46        0       0
[COLOR=Sienna]UUID=174AC7022D706F8D[/COLOR] /DriveH         auto    defaults,umask=007,gid=46        0       0Then do a sudo mount -a

---

### Post by hariks0 on 2010-07-04
Hey,

I just changed the UUDIs and fs_type of both partitions and rebooted.:D

IT MOUNTED WITHOUT ANY PROBLEM !:popcorn:

Thank you all.

---

