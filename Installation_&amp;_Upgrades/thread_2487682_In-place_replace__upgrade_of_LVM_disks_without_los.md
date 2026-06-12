---
title: "In-place replace / upgrade of LVM disks without losing data?"
date: 2023-06-12
forum: Installation &amp; Upgrades
---

### Post by edflecko on 2023-06-12
I have a server with twelve (12) SAS drives that make up my LVM group/disk. Each drive is twelve (12) TB and I'd like to replace / upgrade all disks with twenty (20) TB disks.

Is there a way to upgrade the entire LVM by replacing the 12 TB disks with the 20 TB disks without losing any data? Maybe it's possible to replace the disks one at a time and then resize the entire LVM to utilize all of the new space once I'm completed?

Thank you,
Ed

---

### Post by MAFoElffen on 2023-06-12
Back up the data first, then prep the disks for LVM, then add them to the VG. Then move the data off the other disks you want to remove. Then remove the old disks from the VG...

Example is like this...Say the new disk is '/dev/sdv' and the target VG is named vg-data. This is a VM is spun up to use as an example for this...
```

NAME                  MOUNTPOINT         SIZE FSTYPE      TYPE
sda                                       35G             disk
&#9500;&#9472;sda1                /boot/efi            1G vfat        part
&#9500;&#9472;sda2                /boot                2G ext4        part
&#9500;&#9472;sda3                                     6G LVM2_member part
&#9474; &#9492;&#9472;vg--swap-lv--swap [SWAP]               6G swap        lvm
&#9500;&#9472;sda4                                    18G LVM2_member part
&#9474; &#9492;&#9472;vg--root-lv--root /                   18G ext4        lvm
&#9492;&#9472;sda5                                   7.9G LVM2_member part
  &#9492;&#9472;vg--home-lv--home /home              7.9G ext4        lvm
sdb                                        1G             disk
&#9492;&#9472;sdb1                                  1022M LVM2_member part
  &#9492;&#9472;vg--data-lv--data /data              3.2G ext4        lvm
sdc                                        1G             disk
&#9492;&#9472;sdc1                                  1022M LVM2_member part
  &#9492;&#9472;vg--data-lv--data /data              3.2G ext4        lvm
sdd                                        1G             disk
&#9492;&#9472;sdd1                                  1022M LVM2_member part
  &#9492;&#9472;vg--data-lv--data /data              3.2G ext4        lvm
sde                                        1G             disk
&#9492;&#9472;sde1                                  1022M LVM2_member part
  &#9492;&#9472;vg--data-lv--data /data              3.2G ext4        lvm
sdf                                        2G             disk
sdg                                        2G             disk
sdh                                        2G             disk
sdi                                        2G             disk
sr0                                     1024M             rom

```
You can see that VG vg-data, LV lv-data is made up of multiple 1G disks. Like you, I have larger disks there that I will replace the smaller disks with... First with gdisk, adding GPT LVM partitions:
```

root@lvm-test-server1:/home/mafoelffen# gdisk /dev/sdf
GPT fdisk (gdisk) version 1.0.8

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries in memory.

Command (? for help): o
This option deletes all partitions and creates a new protective MBR.
Proceed? (Y/N): y

Command (? for help): n
Partition number (1-128, default 1): 
First sector (34-4194270, default = 2048) or {+-}size{KMGTP}: 
Last sector (2048-4194270, default = 4194270) or {+-}size{KMGTP}: 
Current type is 8300 (Linux filesystem)
Hex code or GUID (L to show codes, Enter = 8300): 8e00
Changed type of partition to 'Linux LVM'

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sdf.
The operation has completed successfully.
## ETC, ETC, until you partiton all the new disks...

```
The prep the disk partitions as LVM
```

root@lvm-test-server1:/home/mafoelffen# pvcreate /dev/sd[f-i]1
  Physical volume "/dev/sdf1" successfully created.
  Physical volume "/dev/sdg1" successfully created.
  Physical volume "/dev/sdh1" successfully created.
  Physical volume "/dev/sdi1" successfully created.

```
Add the new PV's to vg-data
```

root@lvm-test-server1:/home/mafoelffen# vgextend vg-data /dev/sd[f-i]1
  Volume group "vg-data" successfully extended

```
Move the data off of the old disks, onto the new...
```

root@lvm-test-server1:/home/mafoelffen# pvmove /dev/sdb1
  /dev/sdb1: Moved: 2.75%
  /dev/sdb1: Moved: 100.00%
root@lvm-test-server1:/home/mafoelffen# vgreduce vg-data /dev/sdb1
  Removed "/dev/sdb1" from volume group "vg-data"
root@lvm-test-server1:/home/mafoelffen# pvmove /dev/sdc1
  /dev/sdc1: Moved: 2.35%
  /dev/sdc1: Moved: 100.00%
root@lvm-test-server1:/home/mafoelffen# vgreduce vg-data /dev/sdc1
  Removed "/dev/sdc1" from volume group "vg-data"
root@lvm-test-server1:/home/mafoelffen# pvmove /dev/sdd1
  /dev/sdd1: Moved: 1.96%
  /dev/sdd1: Moved: 100.00%
root@lvm-test-server1:/home/mafoelffen# vgreduce vg-data /dev/sdd1
  Removed "/dev/sdd1" from volume group "vg-data"
root@lvm-test-server1:/home/mafoelffen# pvmove /dev/sde1
  /dev/sde1: Moved: 7.84%
  /dev/sde1: Moved: 100.00%
root@lvm-test-server1:/home/mafoelffen# vgreduce vg-data /dev/sde1
  Removed "/dev/sde1" from volume group "vg-data"

```
Check it
```

root@lvm-test-server1:/home/mafoelffen# pvs -o+pv_used
  PV         VG      Fmt  Attr PSize    PFree    Used   
  /dev/sda3  vg-swap lvm2 a--    <6.00g       0   <6.00g
  /dev/sda4  vg-root lvm2 a--   <18.00g       0  <18.00g
  /dev/sda5  vg-home lvm2 a--    <7.95g       0   <7.95g
  /dev/sdb1          lvm2 ---  1022.00m 1022.00m      0 
  /dev/sdc1          lvm2 ---  1022.00m 1022.00m      0 
  /dev/sdd1          lvm2 ---  1022.00m 1022.00m      0 
  /dev/sde1          lvm2 ---  1022.00m 1022.00m      0 
  /dev/sdf1  vg-data lvm2 a--    <2.00g    4.00m   1.99g
  /dev/sdg1  vg-data lvm2 a--    <2.00g  820.00m  <1.20g
  /dev/sdh1  vg-data lvm2 a--    <2.00g   <2.00g      0 
  /dev/sdi1  vg-data lvm2 a--    <2.00g   <2.00g      0 

```
Remove the old empty PV's
```

root@lvm-test-server1:/home/mafoelffen# pvremove /dev/sd[b-e]1
  Labels on physical volume "/dev/sdb1" successfully wiped.
  Labels on physical volume "/dev/sdc1" successfully wiped.
  Labels on physical volume "/dev/sdd1" successfully wiped.
  Labels on physical volume "/dev/sde1" successfully wiped.

```
Check
```

NAME                  MOUNTPOINT         SIZE FSTYPE      TYPE
sda                                       35G             disk
&#9500;&#9472;sda1                /boot/efi            1G vfat        part
&#9500;&#9472;sda2                /boot                2G ext4        part
&#9500;&#9472;sda3                                     6G LVM2_member part
&#9474; &#9492;&#9472;vg--swap-lv--swap [SWAP]               6G swap        lvm
&#9500;&#9472;sda4                                    18G LVM2_member part
&#9474; &#9492;&#9472;vg--root-lv--root /                   18G ext4        lvm
&#9492;&#9472;sda5                                   7.9G LVM2_member part
  &#9492;&#9472;vg--home-lv--home /home              7.9G ext4        lvm
sdb                                        1G             disk
&#9492;&#9472;sdb1                                  1022M             part
sdc                                        1G             disk
&#9492;&#9472;sdc1                                  1022M             part
sdd                                        1G             disk
&#9492;&#9472;sdd1                                  1022M             part
sde                                        1G             disk
&#9492;&#9472;sde1                                  1022M             part
sdf                                        2G             disk
&#9492;&#9472;sdf1                                     2G LVM2_member part
  &#9492;&#9472;vg--data-lv--data /data              3.2G ext4        lvm
sdg                                        2G             disk
&#9492;&#9472;sdg1                                     2G LVM2_member part
  &#9492;&#9472;vg--data-lv--data /data              3.2G ext4        lvm
sdh                                        2G             disk
&#9492;&#9472;sdh1                                     2G LVM2_member part
sdi                                        2G             disk
&#9492;&#9472;sdi1                                     2G LVM2_member part
sr0                                     1024M             rom

```
Questions or more info needed?

---

### Post by edflecko on 2023-06-15
Thank you!

Ed

---

