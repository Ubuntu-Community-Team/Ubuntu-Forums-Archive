---
title: "Need help installing grub"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by kseise on 2008-10-06
I can't get grub to install I have the following drives:
sata 1 2 GB /boot and 48 GB RAID0 /root
sata 2 2 GB swap and 59 GB RAID0 / root (shared with sata 1)
sata 3 500 GB RAID1 /home
sata 4 500 GB RAID1 /home (shared with sata 3)

ide 1 60 GB Vista Install 428 GB /old_data  2 GB Swap

Grub won't install on the RAID drives and won't install on the IDE drive.  FDISK -LU shows the ide drive is (sde) with the correct paritions, but GRUB install fails because no GRUB is installed on the drive.  

Can anybody tell me how to install grub on this setup?

---

### Post by caljohnsmith on 2008-10-06
How about first posting:
```
sudo fdisk -lu
```
So we can get a better picture of your setup.

---

### Post by kseise on 2008-10-06
Good point.  Here you go.
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b770e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   972848204   486424071   fd  Linux raid autodetect
/dev/sda2   *   972848205   976768064     1959930   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00054b3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   972848204   486424071   fd  Linux raid autodetect
/dev/sdb2       972848205   976768064     1959930   82  Linux swap / Solaris

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a4767

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   152328329    76164133+  83  Linux

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/hdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00089f5c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   120005549    60002743+   7  HPFS/NTFS
/dev/hdb2       120005550   799040969   339517710   83  Linux
/dev/hdb3   *   970920405   976768064     2923830   83  Linux
ubuntu@ubuntu:~$ 


```

---

### Post by caljohnsmith on 2008-10-06
So can you specify in BIOS to have any of those drives be first to boot on start up, or does your BIOS limit you? 

Also, please post:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```

---

### Post by kseise on 2008-10-06
> **caljohnsmith said:**
> So can you specify in BIOS to have any of those drives be first to boot on start up, or does your BIOS limit you? 

Also, please post:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```

The BIOS will let me pick which ever one I want.
```

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> 

grub> find /grub/stage1
find /grub/stage1
 (hd1,1)
grub> 


```

---

### Post by kseise on 2008-10-06
I also tried the following:
```

grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> find /grub/stage1
find /grub/stage1
 (hd1,1)
grub> root (hd1)        
root (hd1)
grub> setup (hd1)
setup (hd1)

Error 17: Cannot mount selected partition
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
grub> root (hd0)
root (hd0)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
grub> setup (hd1)
setup (hd1)

Error 17: Cannot mount selected partition
grub> 

```

---

### Post by caljohnsmith on 2008-10-06
OK, try the following which should install Grub to the MBR of (hd1):
```
sudo grub
grub> geometry (hd1)
grub> root (hd1,1)
grub> setup (hd1)
grub> quit
```
Please post the output of the above commands.

---

### Post by kseise on 2008-10-06
I got into Ubuntu, but I had to mess with grub at boot time and edit the menu to boot from (hd1,0).

It did not detect my Vista installation though.

From inside the working Ubuntu, I get:

```

kseise@blackbox:~$ sudo grub
[sudo] password for kseise: 
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> geometry (hd1)
geometry (hd1)
drive 0x81: C/H/S = 60801/255/63, The number of sectors = 976773168, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0xfd
   Partition num: 1,  Filesystem type unknown, partition type 0x82
grub> root (hd1,1)
root (hd1,1)
grub> setup (hd1)
setup (hd1)

Error 17: Cannot mount selected partition
grub> 

```

---

### Post by caljohnsmith on 2008-10-06
So you get a Grub menu on start up and can boot into Ubuntu if you edit its entry on start up? If that is true, just modify your menu.lst with whatever (hdX,Y) worked to boot Ubuntu:
```
gksudo gedit /boot/grub/menu.lst
```
And change all the Ubuntu entries to use the (hdX,Y) that works. Also be sure to change the "#groot=(hdX,Y)" to use the same as the Ubuntu entries. 

And what exactly was the (hdX,Y) that worked? That will give us some idea how to boot your Windows Vista since we will know whether Ubuntu is on the boot drive or not.

---

### Post by kseise on 2008-10-07
OK, Ubuntu boots from (hd0,1).  I will try to locate Vista, but I have to head to work (Windows Only) and will be gone for several hours.  I will report my findings later tonight.  Thanks again for the help.

---

### Post by kseise on 2008-10-07
I GOT IT !!!!

title Microsoft Windows Vista
rootnoverify (hd4,0)
chainloader (hd4,0)+1

Works like a charm.  Thank you so much for your help.  I am back to beta testing Intrepid.  Thank You.

---

### Post by caljohnsmith on 2008-10-07
That's great news you got it working, and I'm glad I could help out. Cheers and have fun. :)

---

