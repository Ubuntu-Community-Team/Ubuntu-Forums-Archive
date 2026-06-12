---
title: "slow boot by fsck in 10.04"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by bragaa on 2010-08-05
hi all,

I've upgrade to 10.04 and I've notice some problems. Particularly, boot takes 1-2 minutes. I tried to investigate it and found the delay occurs just after running init-scripts/bottom, and probably during an fsck.

Here is the output of the relevant part in dmesg's output :
----
[    1.493360]  sda: sda1 < sda5 sda6 sda7 sda8 > sda2 sda3
[    1.536723] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.264321] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   18.069949] udev: starting version 151
[   18.101097] Adding 1084348k swap on /dev/sda8.  Priority:-1 extents:1 across:
1084348k 
[   18.139844] lp: driver loaded but no devices found
----
I'm running kernel 2.6.32-22-generic

Please advice me !

---

### Post by varunendra on 2010-08-06
Is sda8 a swap partition or is there a file (1GB) being added as swap?

If unsure, please post the output of
```
sudo fdisk -l
``` (please note that it is small "L" after fdisk)

---

### Post by arunsonnet on 2010-08-08
i've got a similar problem. Here are my dmesg and fdisk outputs 


```
[    3.720179] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   32.182872] udev: starting version 151
[   32.184887] Adding 2136604k swap on /dev/sda8.  Priority:-1 extents:1 across:2136604k 
[   32.217475] lp: driver loaded but no devices found
```


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          25      200781   de  Dell Utility
/dev/sda2   *          26        1217     9566208    7  HPFS/NTFS
/dev/sda3            1217       13965   102400000    7  HPFS/NTFS
/dev/sda4           13965       38913   200399713    f  W95 Ext'd (LBA)
/dev/sda5           13965       26713   102400000    7  HPFS/NTFS
/dev/sda6           33088       38913    46797313+   7  HPFS/NTFS
/dev/sda7           26714       32821    49062478+  83  Linux
/dev/sda8           32822       33087     2136613+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by bragaa on 2010-08-08
> **varunendra said:**
> Is sda8 a swap partition or is there a file (1GB) being added as swap?

If unsure, please post the output of
```
sudo fdisk -l
``` (please note that it is small "L" after fdisk)

Thank you varunendra, the sda8 is for swap, 1 Gb.
do you think it is oversized ; i have 2 Gb on my laptop.

---

### Post by dino99 on 2010-08-08
swap seem ok (max=2*ram)

maybe its time to clean the system a little: install bleachbit and use it as admin (carefully: read what each setting do), gconf-cleaner can be used too (yes to all)

---

### Post by varunendra on 2010-08-08
> **dino99 said:**
> swap seem ok (max=2*ram)

maybe its time to clean the system a little: install bleachbit and use it as admin (carefully: read what each setting do), gconf-cleaner can be used too (yes to all)
+1

Just out of curiosity, I'd like to see output of
```
df -a -h
```

---

### Post by bragaa on 2010-08-08
> **varunendra said:**
> +1

Just out of curiosity, I'd like to see output of
```
df -a -h
```

Well here it is 
```

Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
/dev/sda7              23G   18G  4,3G  81% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
none                 1002M  328K 1002M   1% /dev
none                     0     0     0   -  /dev/pts
none                 1007M  1,3M 1005M   1% /dev/shm
none                 1007M  276K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon         0     0     0   -  /home/brahim/.gvfs

```

---

