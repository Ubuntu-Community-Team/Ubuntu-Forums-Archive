---
title: "Can't mount extra drives after dist-upgrade to gutsy"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by buddachile on 2007-11-15
I just upgraded from feisty to gutsy today using dist-upgrade. This box does not have a monitor or keyboard hooked up which is why I didn't use the gui update manager.

Anyhow, the box has 4 separate drives all ext3 except for one which is ext2 formatted.

The box boots up fine, services start however the 3 extra data drives do not mount. When I try to mount them using for example:

  $ sudo mount /dev/hdd1 /mnt/bak

I get:

   mount: /dev/hdd1 already mounted or /mnt/bak busy

If I try to unmount it with umount the drive I get a message saying it is not mounted.

What is happening here? How can I fix this problem?

---

### Post by taurus on 2007-11-15
Can you post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by buddachile on 2007-11-15
```

$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003f641

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        3649    29061585    5  Extended
/dev/hda5              32        3649    29061553+  8e  Linux LVM

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a2b31

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       48641   390708801   83  Linux

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003de0b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       30401   244196001   83  Linux

```

```

$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1 /mnt/jukebox ext3 defaults,errors=remount-ro 0 0
# /dev/hdd1 -- converted during upgrade to edgy
UUID=58a9b2fd-4257-4a8b-b2ed-7f91042f08a3 /mnt/bak ext3 defaults,errors=remount-ro 0 0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1 -- converted during upgrade to edgy
UUID=e8987098-eae5-4f67-bcf8-33901c49b324 /boot ext3 defaults 0 2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /mnt/extra_data ext2    defaults,errors=remount-ro 0       0

```
```

$ df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                       27G   11G   15G  41% /
varrun                474M  224K  474M   1% /var/run
varlock               474M  4.0K  474M   1% /var/lock
udev                  474M   96K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   35M  440M   8% /lib/modules/2.6.22-14-386/volatile

```

---

### Post by taurus on 2007-11-15
Try

```
sudo mount -t ext3 /dev/hdd1 /mnt/bak
df -h
```

---

### Post by buddachile on 2007-11-15
I got the following:

```


$ sudo mount -t ext3 /dev/hdd1 /mnt/bak

mount: /dev/hdd1 already mounted or /mnt/bak busy


$ df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root  27G   11G   15G  41% /
varrun                474M  224K  474M   1% /var/run
varlock               474M  4.0K  474M   1% /var/lock
udev                  474M   96K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   35M  440M   8% /lib/modules/2.6.22-14-386/volatile


```

---

### Post by buddachile on 2007-11-16
OK, I figured it out. In /etc/fstab I needed to add /mapper after /dev for instances of the devices (for example modify /dev/hdd1 to /dev/mapper/hdd1). Likewise the command

```
 sudo mount -t ext3 /dev/hdd1 /mnt/bak 
```

needs to be modified to

```
 sudo mount -t ext3 /dev/mapper/hdd1 /mnt/bak 
```

---

