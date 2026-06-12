---
title: "intel ich7 sata raid woes"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by ianare on 2006-11-18
Hey all,

I am trying to install ubuntu 6.10 on a SATA RAID 0 setup with 2 80 GB disks. I can't get the installer or gParted to recognize it. Here is my relevent info:

82801GR/GH (ICH7 Family) Serial ATA

```
root@ubuntu:~# dmraid -ay -v
INFO: Activating GROUP RAID set "isw_dchfhhafgd"
```

```
root@ubuntu:~# fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       14661    35841015   83  Linux
/dev/sda3           14662       15196     4297387+  82  Linux swap / Solaris
/dev/sda4   *       15197       19457    34226482+  a5  FreeBSD

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

```

```
root@ubuntu:~# ls /dev/mapper/
control
```

So it appears that dmraid can load the driver correctly, but I don't see the correct partition info, and I can't mount it. The installer and gparted also fail to recognize anything other than sda and sdb.

I know for a fact this setup WILL work in Linux, since I have fedora core 5 on the Linux partition, win XP on the windows partition, and GRUB. I don't want to format the windows partition.

I wanted to upgrade to ubuntu after seeing how easy and painless it was to set up and use at work, but am having second thoughts now...

Any help is appreciated

---

### Post by mikeputnam on 2006-11-26
I too am having similar woes.  Eagerly awaiting some help on this thread.

Mike Putnam

---

