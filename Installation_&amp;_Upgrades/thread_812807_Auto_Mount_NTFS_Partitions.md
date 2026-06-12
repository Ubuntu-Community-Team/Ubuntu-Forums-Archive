---
title: "Auto Mount NTFS Partitions"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by El King on 2008-05-30
Hey everyone,
i want to know how can i mount my 2 NTFS partitions everytime i open ubuntu. Because now i have to mount them everytime manually!!
here is my fdisk -l
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e8d1e8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       30401   141797722+   f  W95 Ext'd (LBA)
/dev/sda5           12749       23624    87361438+   7  HPFS/NTFS
/dev/sda6           23625       30118    52163023+  83  Linux
/dev/sda7           30119       30401     2273166   82  Linux swap / Solaris

```

---

### Post by sisco311 on 2008-05-30
Edit the /etc/fstab:
```
gksu gedit /etc/fstab
```and add this lines
> /dev/sda1 /media/**windows** ntfs defaults,umask=007,gid=46 0 1
/dev/sda5 /media/**data** ntfs defaults,umask=007,gid=46 0 1Create the mount points:
```
sudo mkdir /media/**windows**
sudo mkdir /media/**data**
```remount the partitions:
```
sudo umount /dev/sda1 /dev/sda5
sudo mount -a
```

---

### Post by El King on 2008-05-30
Great !
Thankz

---

