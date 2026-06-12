---
title: "mdadm RAID1 rename on reboot"
date: 2015-04-22
forum: Installation &amp; Upgrades
---

### Post by Rafael_ on 2015-04-22
Ubuntu server 14.04 LTS 64bits updated.
mdadm - v3.2.5

I'm trying build with mdadm a raid 1 ( 2 disks more 1 spare), but /dev/md0 change on reboot to /dev/md/ubuntu\:0 (server name is ubuntu) .
It's a test VM with 3 512Mb disks sdb, sdc, sdd.

I done this steps:
Prepare disks.
```

parted -a optimal /dev/sdb 
mklabel gpt
mkpart 1 -1
align-check optimal 1

```

Make the RAID 1
```

mdadm --create --verbose /dev/md0 -l 1 -n 2 /dev/sdb1 /dev/sdc1 -x 1 /dev/sdd1
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
mkfs.ext4 /dev/md0
mkdir /raid
mount /dev/md0 /raid/
echo "/dev/md0 /raid ext4 noatime,rw 0 0" >> /etc/fstab

```

Verify if works
```

mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Apr 22 10:57:10 2015
     Raid Level : raid1
     Array Size : 521920 (509.77 MiB 534.45 MB)
  Used Dev Size : 521920 (509.77 MiB 534.45 MB)
   Raid Devices : 2
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Wed Apr 22 10:57:12 2015
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

           Name : ubuntu:0  (local to host ubuntu)
           UUID : e0ac5c4f:0926addd:84d5b6f2:475ea99a
         Events : 17
    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1

       2       8       49        -      spare   /dev/sdd1

df -H
Sist. Arq.                   Tam. Usado Disp. Uso% Montado em
/dev/mapper/ubuntu--vg-root  7,6G  1,4G  5,8G  19% /
none                         4,1k     0  4,1k   0% /sys/fs/cgroup
udev                         246M  4,1k  246M   1% /dev
tmpfs                         52M  459k   51M   1% /run
none                         5,3M     0  5,3M   0% /run/lock
none                         257M     0  257M   0% /run/shm
none                         105M     0  105M   0% /run/user
/dev/sda1                    247M   39M  196M  17% /boot
/dev/md0                     510M  2,4M  476M   1% /raid

```
Why it's happening, or what I did wrong?

---

