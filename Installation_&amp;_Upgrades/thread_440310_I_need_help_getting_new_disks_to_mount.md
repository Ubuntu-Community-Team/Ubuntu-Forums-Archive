---
title: "I need help getting new disks to mount"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by sgg on 2007-05-11
I have installed an SATA JBOD array using using a port multiplier.
The system sees the drives. I was able to partition them using gparted.
I've editied my fstab accordingly. I've used the mount -a command.
I've rebooted. No matter what I do, when I df -h these drives dont show. 

I'm running Ubuntu 6.06 Server w/ubuntu desktop installed.

Here is the output from df -h :
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  3.4G   64G   5% /
varrun                471M   88K  470M   1% /var/run
varlock               471M  4.0K  471M   1% /var/lock
udev                  471M  156K  470M   1% /dev
devshm                471M     0  471M   0% /dev/shm

```



from fdisk -l :
 ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  3.4G   64G   5% /
varrun                471M   88K  470M   1% /var/run
varlock               471M  4.0K  471M   1% /var/lock
udev                  471M  156K  470M   1% /dev
devshm                471M     0  471M   0% /dev/shm
vfx@jupiter:~$ sudo mount -a
Password:
mount: /dev/sdg1 already mounted or /media/apollo1 busy
mount: /dev/sdd1 already mounted or /media/apollo4 busy
mount: /dev/sdc5 already mounted or /media/apollo5 busy
mount: /dev/sdc6 already mounted or /media/apollo6 busy
vfx@jupiter:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  3.4G   64G   5% /
varrun                471M   88K  470M   1% /var/run
varlock               471M  4.0K  471M   1% /var/lock
udev                  471M  156K  470M   1% /dev
devshm                471M     0  471M   0% /dev/shm
vfx@jupiter:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9375    75304656   83  Linux
/dev/sda2            9376        9726     2819407+   5  Extended
/dev/sda5            9376        9726     2819376   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001    5  Extended
/dev/sdc5               1       44619   358402054+  83  Linux
/dev/sdc6           44620       91201   374169883+  83  Linux

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001   83  Linux

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91201   732572001   83  Linux

Disk /dev/sdf: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       91201   732572001   83  Linux

Disk /dev/sdg: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       91201   732572001   83  Linux
vfx@jupiter:~$


```

---

