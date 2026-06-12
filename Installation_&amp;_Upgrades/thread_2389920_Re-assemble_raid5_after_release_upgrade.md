---
title: "Re-assemble raid5 after release upgrade"
date: 2018-04-23
forum: Installation &amp; Upgrades
---

### Post by anytimesoon2 on 2018-04-23
I upgraded from 14.04 to 16.04 this morning using the do-release-upgrade command.

This finished the upgrade with the system unable to reboot. 

I reinstalled ubuntu over the old partition, and now I can't see my raid partition.

Is there any way to re-assemble a raid5 without losing any of the data on there? (It's not backed up... I know... I know)

---

### Post by anytimesoon2 on 2018-04-23
UPDATE:

running `mdadm --examine /dev/sd[acd] >> raid.status` gets the following output


mdad/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bda4d60b:67008be9:82345b45:2c2b7f6c
           Name : Apollo:0  (local to host Apollo)
  Creation Time : Sun Nov 29 16:01:11 2015
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 3906764672 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906764672 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=2352 sectors
          State : clean
    Device UUID : 5dae3657:4f6544ca:ab4386db:888d9356

    Update Time : Mon Apr 23 10:17:31 2018
       Checksum : c36c3e96 - correct
         Events : 677684

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing, 'R' == replacing)

/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bda4d60b:67008be9:82345b45:2c2b7f6c
           Name : Apollo:0  (local to host Apollo)
  Creation Time : Sun Nov 29 16:01:11 2015
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 3906764672 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906764672 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=304 sectors
          State : clean
    Device UUID : 3c6435e2:10604cd8:6b457ac1:1e4342b1

    Update Time : Mon Apr 23 10:17:31 2018
       Checksum : 9d159fba - correct
         Events : 677684

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing, 'R' == replacing)


/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bda4d60b:67008be9:82345b45:2c2b7f6c
           Name : Apollo:0  (local to host Apollo)
  Creation Time : Sun Nov 29 16:01:11 2015
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 3906764672 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906764672 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=304 sectors
          State : clean
    Device UUID : 7851bd6d:c63ed060:240daf01:f7aaedb2

    Update Time : Mon Apr 23 10:17:31 2018
       Checksum : f3019a0e - correct
         Events : 677684

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing, 'R' == replacing)



So everything is still there, I'm just not sure how to reassemble

---

### Post by anytimesoon2 on 2018-04-23
I tried:

mdadm --assemble --force /dev/md0 /dev/sda /dev/sdc1 /dev/sdd1

Which output:
mdadm: /dev/sda is busy - skipping
mdadm: /dev/sdc1 is busy - skipping
mdadm: /dev/sdd1 is busy - skipping

---

### Post by anytimesoon2 on 2018-04-23
running mdadm -D /dev/md0

returns this:

/dev/md0:
        Version : 1.2
  Creation Time : Sun Nov 29 16:01:11 2015
     Raid Level : raid5
     Array Size : 3906764672 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 1953382336 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Mon Apr 23 10:17:31 2018
          State : clean 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : Apollo:0  (local to host Apollo)
           UUID : bda4d60b:67008be9:82345b45:2c2b7f6c
         Events : 677684

    Number   Major   Minor   RaidDevice State
       4       8        0        0      active sync   /dev/sda
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1




Does this mean it's running properly and just needs mounting?

---

### Post by anytimesoon2 on 2018-04-23
I've tried mounting it using:

mount /dev/md0 /mnt/

and it returned this:

mount: /dev/md0: more filesystems detected. This should not happen,
       use -t <type> to explicitly specify the filesystem type or
       use wipefs(8) to clean up the device.


I can't remember the filesystem I initially had it on. I think it was ext4.

The individual drives say that their filesystem is 'linux_raid_memb'

---

