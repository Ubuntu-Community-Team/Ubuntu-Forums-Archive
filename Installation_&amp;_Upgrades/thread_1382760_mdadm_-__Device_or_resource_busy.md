---
title: "mdadm -  Device or resource busy"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by oehq on 2010-01-16
Hello,
I am trying to set up a mdadm raid in a new machine that I am building as a home theatre PC.
any help here would be greatly appreciated.

the machine boot just fine from /dev/sdc running ubuntu 9.10
However in gparted /dev/sda and dev/sdb show to be part of /devmapper/sil_ajbicfacbaej

Both dev/sda and /dev/sdb were drives that used to be part of a sil hardware raid on a previous machine. I would like to use them as a new mdadm raid on this new machine the old hardware card was really quite slow. the drives are now pluged into the MB and should be much faster there.


**fdisk -l shows this**
***********************************************
heffsvr2@heffsvr-2:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cc314

Device Boot Start End Blocks Id System

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cc314

Device Boot Start End Blocks Id System

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e95c0

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 29367 235890396 83 Linux
/dev/sdc2 29368 30401 8305605 5 Extended
/dev/sdc5 29368 30401 8305573+ 82 Linux swap / Solaris
************************************************
**cat /proc/mdstat show the folowing**

heffsvr2@heffsvr-2:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>
**************************************************
**Creating mdadm produces the following**

heffsvr2@heffsvr-2:~$ sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda /dev/sdb
mdadm: Cannot open /dev/sda: Device or resource busy
mdadm: Cannot open /dev/sdb: Device or resource busy

************************************************** ******
I tried the command
**sudo dmsetup remove /dev/mapper/sil_ajbicfacbaej**

it produces no errors but does not remove it.
Any Ideas as to how to start over and use these drives in mdadm??

Thanks for your help

---

