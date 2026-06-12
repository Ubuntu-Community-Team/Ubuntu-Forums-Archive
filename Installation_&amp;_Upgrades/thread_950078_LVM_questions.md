---
title: "LVM questions"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-10-16
I have installed a while back lvm on my desktop.
My hard disk space is getting tied:

> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/lvmvolume-root
                       49G  8.0G   38G  18% /
varrun                1.5G  348K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
procbususb            1.5G  116K  1.5G   1% /proc/bus/usb
udev                  1.5G  116K  1.5G   1% /dev
devshm                1.5G  612K  1.5G   1% /dev/shm
lrm                   1.5G   44M  1.5G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1              99M   66M   28M  71% /boot
/dev/mapper/lvmvolume-home
                       97G   89G  2.6G  98% /home
/dev/sdb1              40G   38G  1.3G  97% /media/hdc1
/dev/sdb3              56G  9.7G   43G  19% /media/hdc3
/dev/sdb5              40G   27G   13G  67% /media/hdc5
/dev/sdb6              50G   46G  4.4G  92% /media/hdc6
/dev/sdc1              79G   73G  6.0G  93% /media/hdd1
/dev/sdc5              71G   60G   11G  85% /media/hdd5
/dev/mapper/lvmvolume-var
                       49G   33G   14G  71% /var
gvfs-fuse-daemon       49G  8.0G   38G  18% /home/ronald/.gvfs
tmpfs                 1.5G   44M  1.5G   3% /lib/modules/2.6.24-21-generic/volatile


I think there would be still 49G free:
> sudo vgdisplay
  --- Volume group ---
  VG Name               lvmvolume
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                4
  Open LV               4
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               251.41 GB
  PE Size               4.00 MB
  Total PE              64361
  Alloc PE / Size       52560 / 205.31 GB
  Free  PE / Size       11801 / 46.10 GB
  VG UUID               DEFVsZ-p79S-cqHh-JduY-iXr6-gnDZ-R4NfyE


oder more?
>  sudo fdisk -l
[sudo] password for ronald: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027078

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   83  Linux
/dev/sda2              14        6093    48837600    7  HPFS/NTFS
/dev/sda3            6094       38913   263626650   8e  Linux LVM

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d612d60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100       17021    95763465    f  W95 Ext'd (LBA)
/dev/sdb3           17022       24321    58637250   83  Linux
/dev/sdb5            5100       10198    40957686    7  HPFS/NTFS
/dev/sdb6           10199       16708    52291543+   7  HPFS/NTFS
/dev/sdb7           16709       17021     2514141   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45dc45db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sdc2           10200       19457    74364885    f  W95 Ext'd (LBA)
/dev/sdc5           10200       19457    74364853+   b  W95 FAT32


Questions:
1. How can I find out how much space I still have?
2. How do I use that free space?
3. Since my /home ran out, I used 20G already from /var
How can I reduce /var and add it to /home ?


bye

R.

---

