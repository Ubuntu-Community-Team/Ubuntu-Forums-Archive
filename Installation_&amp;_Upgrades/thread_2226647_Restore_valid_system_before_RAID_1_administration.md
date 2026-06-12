---
title: "Restore valid system before RAID 1 administration"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by camille2 on 2014-05-28
Hello,

I'm new here. I don't know if i give you enough informations.
After a failure during rebuild process on my RAID 1 system, i had to desabled RAID activity and i have now 2 independant disks.
The first one seems to be corrupted with many system errors. The second one contain my datas in a safe partition but when i boot on it i have an error /boot/efi is not ready or present ...i need to press S to get my session.

sdb with my datas :

```
sudo parted -s /dev/sdb unit s print
Modèle: ATA ST2000VX000-1CU1 (scsi)
Disque /dev/sdb : 3907029168s
Taille des secteurs (logiques/physiques): 512B/4096B
Table de partitions : gpt

Numéro  Début        Fin          Taille       Système de fichiers  Nom  Fanions
 1      2048s        194559s      192512s      fat32                     msftdata
 2      194560s      3873554431s  3873359872s  ext4                      msftdata
 3      3873554432s  3907028991s  33474560s    linux-swap(v1)

lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   1,8T  0 disk 

sdb      8:16   0   1,8T  0 disk 
&#9500;&#9472;sdb1   8:17   0    94M  0 part /media/me/BD5B-5887
&#9500;&#9472;sdb2   8:18   0   1,8T  0 part /
&#9492;&#9472;sdb3   8:19   0    16G  0 part 
sr0     11:0    1  1024M  0 rom  

mount
/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/dev/sda2 on /media/me/298ed3f6-593d-4fab-bced-b98ebb159ead type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb1 on /media/me/BD5B-5887 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,flush,uhelper=udisks2)
```


I would like to restore correctly my sdb disk before any other action. How can i do that safely. Can i copy sdb partitions on my sda disk even if i have lost my bootable partition and then reactivate RAID 1 ?

Thank you for your answers

---

