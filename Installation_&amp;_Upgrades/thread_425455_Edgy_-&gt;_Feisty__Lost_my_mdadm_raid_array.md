---
title: "Edgy -&gt; Feisty : Lost my mdadm raid array"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Rob_Quads on 2007-04-27
My machine has a number of disks in it

/dev/hda - Onboard Primary Master (OS)
/dev/hdb - Onboard Primary Slave (Files)
/dev/hdc - Onboard Secondary Master - Not connected
/dev/hdd - Onboard Secondary Slave- Not connected
/dev/hde - PCI Board - Primary Master - RAID - /dev/md0
/dev/hdf - PCI Board - Primary Slave- RAID - /dev/md0
/dev/hdg - PCI Board - Secondary Master- RAID - /dev/md0
/dev/hdh - PCI Board - Secondary Slave- RAID - /dev/md0
/dev/sda - PCI SATA
/dev/sdb - PCI SATA 

I had a raid array /dev/md0 with /dev/hd[efgh] in it and logical volumes /dev/vg00/lv_raid

After upgrading to Fesity all the volume group / logical volume info has gone

How do I get back the array and volume group information etc??

---

### Post by Rob_Quads on 2007-04-27
Bit further but its detecting some of the raid as failed I think

```

root@FileServer:/home/convery# mdadm --assemble  /dev/md0 /dev/hde /dev/hdf /dev/hdg /dev/hdh 
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
root@FileServer:/home/convery# cat /proc/mdstat 
Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] [multipath] [faulty] 
md0 : inactive hde[0](S) hdg[3](S) hdh[2](S) hdf[1](S)
      1172186752 blocks
       
unused devices: <none>

```

Below is the status of each drive

```

root@FileServer:/home/convery# mdadm -E /dev/hd[efgh]
/dev/hde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d41d20ba:89f42c99:1f9c2965:759ec036
  Creation Time : Sat Mar 24 00:00:31 2007
     Raid Level : raid5
    Device Size : 293036096 (279.46 GiB 300.07 GB)
     Array Size : 879108288 (838.38 GiB 900.21 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Apr 27 19:52:05 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 3a2c8c16 - correct
         Events : 0.195044

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0      33        0        0      active sync   /dev/hde

   0     0      33        0        0      active sync   /dev/hde
   1     1      33       64        1      active sync   /dev/hdf
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
/dev/hdf:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d41d20ba:89f42c99:1f9c2965:759ec036
  Creation Time : Sat Mar 24 00:00:31 2007
     Raid Level : raid5
    Device Size : 293036096 (279.46 GiB 300.07 GB)
     Array Size : 879108288 (838.38 GiB 900.21 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Apr 27 19:52:05 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 3a2c8c58 - correct
         Events : 0.195044

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1      33       64        1      active sync   /dev/hdf

   0     0      33        0        0      active sync   /dev/hde
   1     1      33       64        1      active sync   /dev/hdf
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
/dev/hdg:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d41d20ba:89f42c99:1f9c2965:759ec036
  Creation Time : Sat Mar 24 00:00:31 2007
     Raid Level : raid5
    Device Size : 293036096 (279.46 GiB 300.07 GB)
     Array Size : 879108288 (838.38 GiB 900.21 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Apr 27 13:09:11 2007
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 3a2c2d8d - correct
         Events : 0.195016

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3      34        0        3      active sync   /dev/hdg

   0     0      33        0        0      active sync   /dev/hde
   1     1      33       64        1      active sync   /dev/hdf
   2     2      34       64        2      active sync   /dev/hdh
   3     3      34        0        3      active sync   /dev/hdg
/dev/hdh:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d41d20ba:89f42c99:1f9c2965:759ec036
  Creation Time : Sat Mar 24 00:00:31 2007
     Raid Level : raid5
    Device Size : 293036096 (279.46 GiB 300.07 GB)
     Array Size : 879108288 (838.38 GiB 900.21 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Apr 27 19:51:50 2007
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 3a299259 - correct
         Events : 0.195041

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2      34       64        2      active sync   /dev/hdh

   0     0      33        0        0      active sync   /dev/hde
   1     1      33       64        1      active sync   /dev/hdf
   2     2      34       64        2      active sync   /dev/hdh
   3     3       0        0        3      faulty removed
root@FileServer:/home/convery#
```

---

### Post by Rob_Quads on 2007-04-27
```

root@FileServer:/home/convery# mdadm --re-add /dev/md0 /dev/hdg
mdadm: re-added /dev/hdg
root@FileServer:/home/convery# mdadm --re-add /dev/md0 /dev/hdh
root@FileServer:/home/convery# mdadm -R /dev/md0
root@FileServer:/home/convery# cat /proc/mdstat 
Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] [multipath] [faulty] 
md0 : active raid5 hdh[2] hdg[3] hde[0] hdf[1]
      879108288 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

```

Array rebuilt now how to get back the LVM

---

### Post by Rob_Quads on 2007-04-27
After activating the array all the LVM came back so its all rescued BUT

Each time I reboot the raid array dissapears again.  :confused:

---

### Post by Gruelius on 2007-04-29
I have the same problem. I upgraded from 6.10 to feisty and then created the raid and im getting these errors. its a raid 5 array with 5 pata hard disks.


Here are some relevant bits of info

```
Every 2.0s: cat /proc/mdstat                            Sun Apr 29 12:54:54 2007 
 
Personalities : [raid6] [raid5] [raid4] 
md0 : inactive hde[1] hdg[3] hdf[2] 
      586082688 blocks 
 
unused devices: <none> 
```

```
root@tuxserver:~# mdadm --assemble /dev/md0 /dev/hdb /dev/hde /dev/hdf /dev/hdg /dev/hdh 
mdadm: superblock on /dev/hde doesn't match others - assembly aborted 
```

Just like you if i re create it manually it works fine. For some reason it believes two of my disks, hdb and hdh have ext3 file systems on them (The array is ext3 with the stride option set correctly)

```
root@tuxserver:~# mdadm --create /dev/md0 --level=5 --chunk=128 --raid-devices=5 /dev/hdb /dev/hde /dev/hdf /dev/hdg /dev/hdh
mdadm: /dev/hdb appears to contain an ext2fs file system
size=781443584K mtime=Sat Apr 28 18:22:06 2007
mdadm: /dev/hdb appears to be part of a raid array:
level=raid5 devices=5 ctime=Sat Apr 28 15:07:54 2007
mdadm: /dev/hde appears to be part of a raid array:
level=raid5 devices=5 ctime=Sat Apr 28 15:07:54 2007
mdadm: /dev/hdf appears to be part of a raid array:
level=raid5 devices=5 ctime=Sat Apr 28 15:07:54 2007
mdadm: /dev/hdg appears to be part of a raid array:
level=raid5 devices=5 ctime=Sat Apr 28 15:07:54 2007
mdadm: /dev/hdh appears to contain an ext2fs file system
size=835850756K mtime=Thu Apr 19 13:06:56 1973
mdadm: /dev/hdh appears to be part of a raid array:
level=raid5 devices=5 ctime=Sat Apr 28 15:07:54 2007
Continue creating array? y

```.

At the moment im just manually rebuilding and trying to not switch the damn box off!
J

---

### Post by Gruelius on 2007-04-29
[http://ubuntuforums.org/showthread.php?t=410136&highlight=mdadm](http://ubuntuforums.org/showthread.php?t=410136&highlight=mdadm)

This guide has helped me.

---

### Post by Rob_Quads on 2007-04-29
It looks like it was the /etc/mdadm/mdadm.conf file that was zapped which results in it loosing the raid each reboot. After doing the following it now survives a reboot

```

root@FileServer:/home/convery# cat /etc/mdadm/mdadm.conf 
DEVICE partitions
MAILADDR root
root@FileServer:/home/convery# cd /etc/mdadm
root@FileServer:/home/convery# cp mdadm.conf mdadm.conf.`date +%y%m%d`
root@FileServer:/home/convery# echo "DEVICE partitions" > mdadm.conf
root@FileServer:/home/convery# mdadm --detail --scan >> mdadm.conf 

```

---

