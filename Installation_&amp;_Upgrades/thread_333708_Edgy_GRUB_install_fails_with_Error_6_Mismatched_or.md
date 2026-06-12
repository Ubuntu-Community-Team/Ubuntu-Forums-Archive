---
title: "Edgy: GRUB install fails with Error 6: Mismatched or corrupt version of stage1/stage2"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by IntuitiveNipple on 2007-01-07
I'm trying to install Edgy Eft from the Desktop Live CD onto a dmraid RAID 1+0 (Mirror + Stripe) Promise FastTrak TX2000 on a dual Athlon MP server.

I've followed the instructions in the [FakeRAIDHowto](https://help.ubuntu.com/community/FakeRaidHowto) and the modifications to the process in [DMRAID 1.0.0.rc13  modified Howto](http://ubuntuforums.org/showpost.php?p=1708724&postcount=11) and the [SATA RAID Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

I've searched extensively and asked on freenode IRC but there seems to be little information about this error.

I've got no problems accessing the RAID device via /dev/mapper using dmraid 0.9.9+1.0.0.rc9 (rc13 doesn't work - won't activate the Superset with dmraid -ay).

Any suggestions gratefully received!

**Details**

I've partitioned the drive as follows:
```
Disk /dev/mapper/pdc_biieicaii: 121.9 GB, 121999982592 bytes
255 heads, 63 sectors/track, 14832 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_biieicaii1   *           1        3060    24579418+   7  HPFS/NTFS
/dev/mapper/pdc_biieicaii2            3061        8416    43022070    7  HPFS/NTFS
/dev/mapper/pdc_biieicaii3            8417       14832    51536520    5  Extended
/dev/mapper/pdc_biieicaii5            8417        8782     2939863+  82  Linux swap / Solaris
/dev/mapper/pdc_biieicaii6            8783        8845      506016   83  Linux
/dev/mapper/pdc_biieicaii7            8846       11278    19543041   83  Linux
/dev/mapper/pdc_biieicaii8           11279       14832    28547473+  83  Linux
```
Partitions 1 & 2 are the existing Windows installation. Swap is 5, boot is 6, root is 7, home is 8. mount reports:
```
/dev/mapper/pdc_biieicaii7 on /target type ext3 (rw)
/dev/mapper/pdc_biieicaii6 on /target/boot type ext3 (rw)
/dev on /target/dev type none (rw,bind)
proc on /target/proc type proc (rw)
sysfs on /target/sys type sysfs (rw)
/dev/mapper/pdc_biieicaii8 on /target/home type ext3 (rw)
```
 After 'chroot /target' the GRUB session goes like this:
```
grub> device (hd0) /dev/mapper/pdc_biieicaii

grub> find /grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)

Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1" exists... yes
Checking if "/grub/stage2" exists... yes
Checking if "/grub/e2fs_stage1_5" exists... yes
Running "embed /grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded. 
succeeded
Running "install /grub/stage1 (hd0) (hd0)1+15 p (hd0,5)/grub/stage2 /grub/menu.lst"... failed

Error 6: Mismatched or corrupt version of stage1/stage2
```

The directory listing:
```
ls -l /boot/grub/
total 260
-rw-r--r-- 1 root root   7508 2007-01-07 16:48 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2007-01-07 16:48 fat_stage1_5
-rw-r--r-- 1 root root   8128 2007-01-07 16:48 jfs_stage1_5
-rw-r--r-- 1 root root   6804 2007-01-07 16:48 minix_stage1_5
-rw-r--r-- 1 root root   9076 2007-01-07 16:48 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-01-07 23:30 stage1
-rw-r--r-- 1 root root 105652 2007-01-07 23:30 stage2
-rw-r--r-- 1 root root 105652 2007-01-07 23:31 stage2_eltorito
-rw-r--r-- 1 root root   8764 2007-01-07 16:48 xfs_stage1_5
```

I can't install to the underlying devices (hde+hdf, hdg+hdh) manually because the partitions are on the 2nd disk in the stripe.

I also tried installing to both copies of the mirror within GRUB using:
```
grub> device (hd0) /dev/mapper/pdc_biieicaii-0
grub> device (hd0) /dev/mapper/pdc_biieicaii-1
```
but this also reported Error 6.

---

### Post by IntuitiveNipple on 2007-01-08
I'm digging into the source code on this. 

The error "Mismatched or corrupt version..." is an almost generic error that is reported by the error value ERR_BAD_VERSION in stage2/common.c

It is reported for about 6 different error conditions in stage2/builtins.c.

When I have the time I intend modifying the source to make each error-report unique, then running the recompiled version to show precisely where the error is being generated, and thus hopefully work out what the exact cause of the error is.

---

