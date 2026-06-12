---
title: "RAID/LVM cmds to migrate to larger drives"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by static0verdrive on 2010-09-27
Hi guys,

I was wondering if you could help me figure out how to migrate my whole server to larger hard drives (i.e. I'd like to replace my four 1TB's with four 2TB's, for a new total of 4TB instead of 2TB)... I'll post the output from everything (relevant) that I can think of in code tags below, but if I miss something please tell me.

I'd like to end up with much larger **/home** and **/public** partitions. When I first set up raid and then LVM it seemed like it wouldn't be too hard once this day arrived, but I've had little luck finding help online for upgrades and resizing versus simply rebuilding from a failure. Specifically, I figure I have to mirror the data over to the new drives one at a time, but I can't figure out how to build the raid partitions on the new disks in order to have more space (yet mirror with the old drive that has a smaller partition)... don't the raid partitions have to be the same size to mirror? :confused: Any help would be greatly appreciated!

_Ubuntu Server (karmic) 2.6.31-22-server #65-Ubuntu SMP; fully updated_

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md5 : active raid1 sdd5[1] sdc5[0]
      968952320 blocks [2/2] [UU]
      
md1 : active raid1 sdd1[1] sdc1[0]
      3903680 blocks [2/2] [UU]
      
md3 : active raid0 sdc2[0] sdd2[1]
      7807360 blocks 64k chunks
      
md2 : active raid1 sdb2[1] sda2[0]
      7815552 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[1] sda1[0]
      248896 blocks [2/2] [UU]
      
md4 : active raid1 sda5[0] sdb5[1]
      968695296 blocks [2/2] [UU]
      
unused devices: <none>

===================

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              3.7G  824M  2.6G  24% /
udev                  1.9G  304K  1.9G   1% /dev
none                  1.9G     0  1.9G   0% /dev/shm
none                  1.9G  300K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/md0              236M   21M  196M  10% /boot
/dev/mapper/GREYMALKIN-HOME
                      138G   20G  112G  15% /home
/dev/mapper/GREYMALKIN-VAR--TMP
                       56G  180M   51G   1% /var/tmp
/dev/mapper/GREYMALKIN-PUBLIC
                      1.6T  1.2T  372G  76% /public
/dev/md2              7.4G  1.4G  5.5G  20% /usr

===================

pvdisplay

  --- Physical volume ---
  PV Name               /dev/md4
  VG Name               GREYMALKIN
  PV Size               923.82 GB / not usable 3.50 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              236497
  Free PE               0
  Allocated PE          236497
  PV UUID               64a59X-NtRp-02Mu-P7LT-i8Hs-JJez-gld3HJ
   
  --- Physical volume ---
  PV Name               /dev/md5
  VG Name               GREYMALKIN
  PV Size               924.06 GB / not usable 2.50 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              236560
  Free PE               0
  Allocated PE          236560
  PV UUID               VZtyVl-UIF6-aC3n-sER1-KEqJ-rehL-kdGRe4
   

vgdisplay

  --- Volume group ---
  VG Name               GREYMALKIN
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               3
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               1.80 TB
  PE Size               4.00 MB
  Total PE              473057
  Alloc PE / Size       473057 / 1.80 TB
  Free  PE / Size       0 / 0   
  VG UUID               rsghsk-Vsxd-WCVt-Gweh-TkmQ-WzCA-27gAic
   

lvdisplay

  --- Logical volume ---
  LV Name                /dev/GREYMALKIN/HOME
  VG Name                GREYMALKIN
  LV UUID                532sw3-jC1G-rKFf-8qaD-43Ev-vqpM-VIme1s
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                139.70 GB
  Current LE             35762
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/GREYMALKIN/VAR-TMP
  VG Name                GREYMALKIN
  LV UUID                UjrMaL-Qswf-469J-itPR-KdcD-2qTU-pRJ8F3
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                55.88 GB
  Current LE             14305
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/GREYMALKIN/PUBLIC
  VG Name                GREYMALKIN
  LV UUID                sGK0Vb-ubiS-LFRf-0fyu-Geel-7bWl-i2xVcv
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                1.61 TB
  Current LE             422990
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
  
 
cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/md1 during installation
UUID=49215c22-ddc5-4c20-bc0b-f9baf97331d0 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=f5bbedcf-6ebf-4f80-8de6-fb9e0fc49acb /boot           ext4    defaults        0       2
/dev/mapper/GREYMALKIN-HOME /home           ext4    defaults        0       2
/dev/mapper/GREYMALKIN-PUBLIC /public         ext4    defaults        0       2
# /usr was on /dev/md2 during installation
UUID=294ab205-69fc-41b7-bf81-e01728374f05 /usr            ext4    defaults        0       2
/dev/mapper/GREYMALKIN-VAR--TMP /var/tmp        ext4    defaults        0       2
# swap was on /dev/md3 during installation
UUID=efe9c5dd-c6b0-4e22-86ee-207e91d6cb57 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

Thanks in advance,
--static--

---

### Post by TheSilverRing on 2010-09-30
I am in a very similar scenario, going from 1TB to 2TB also.
 
I was going to pull a 1TB drive then replace with a 2TB, then do the same with the next 1TB the use parted to grow the partition. 
 
Or I may simply DD the entire 1tb drives to the 2TB drivers then change mdadm to use the new drives then grow the partitions. Maybe I will try that first.
 
 
Did you figure something out?

---

### Post by static0verdrive on 2010-10-03
I did just find this link but I could use some advice customizing to my setup...

[http://www.howtoforge.com/how-to-resize-lvm-software-raid1-partitions-shrink-and-grow]("http://www.howtoforge.com/how-to-resize-lvm-software-raid1-partitions-shrink-and-grow")

I'll scan and post a better visual of my hard drives as soon as I can too.

---

### Post by psusi on 2010-10-03
Plug in the new disks and use mdadm to create a new raid array using them.  Then pvcreate and vgextend to initialize the new raid as an lvm physical volume, then pvmove to migrate your volumes over to the new array, and if you then want to get rid of the old disks, vgreduce and pvremove the old array.

Also it sounds like you are using raid 0+1.  You would 6tb of usable space out of a raid5 instead of only 4.

---

