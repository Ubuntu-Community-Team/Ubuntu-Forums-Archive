---
title: "Repairing a RAID array"
date: 2014-02-21
forum: Installation &amp; Upgrades
---

### Post by btkramer on 2014-02-21
I had a drive go out on my RAID array when I restarted the computer after an update. It was working fine before the update, so I figured that maybe the update messed with something, odds are the drive itself didn't fail right at that time it was restarted. so I checked the array.
I ran:



[B]cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc1[2](F) sdd1[3] sdb[4]
      5860535808 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/2] [_U_U]
      
unused devices: <none>[/B]



then:

[B]

sudo mdadm --examine /dev/sd[abcd]1

/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ecabf5:ea889c14:26169875:c4bfdf8c
           Name : Ubuntu-NAS:0
  Creation Time : Fri Oct  5 21:32:19 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b7cf63a5:d093e89a:bfa44323:b9f4cdf5

    Update Time : Sun Jan  5 17:04:36 2014
       Checksum : 7063f998 - correct
         Events : 121158

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ecabf5:ea889c14:26169875:c4bfdf8c
           Name : Ubuntu-NAS:0
  Creation Time : Fri Oct  5 21:32:19 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 9fde527f:4238b936:5f360b53:c6dac84a

    Update Time : Fri Feb 21 19:35:16 2014
       Checksum : 6b254acb - correct
         Events : 133579

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : .AAA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ecabf5:ea889c14:26169875:c4bfdf8c
           Name : Ubuntu-NAS:0
  Creation Time : Fri Oct  5 21:32:19 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ba87cbc8:a3eb76b0:39aeb5e4:076872d7

    Update Time : Fri Feb 21 19:35:57 2014
       Checksum : 4cb0ac84 - correct
         Events : 133597

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : .A.A ('A' == active, '.' == missing)
[/B]



I thought the drive itself should be ok and I decided to zero the superblock of the failed drive from the array and add it back to the array. As I was typing the command to do so, I checked the result of **cat /proc/mdstat** and thought that it was sda1 that had failed, so I typed:

[B]

sudo mdadm --zero-superblock /dev/sda1

sudo mdadm --add /dev/md0 /dev/sda1[/B]

I got the response:

[B]mdadm: /dev/md0 has failed so using --add cannot work and might destroy
mdadm: data on /dev/sda1.  You should stop the array and re-assemble it.[/B]



Looking closer, it looks like it was sdb1 that failed, not sda1, so it appears I have zeroed the wrong superblock. I then tried to assemble the array with:

[B]

sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1[/B]

and got the response:

[B]mdadm: no recogniseable superblock on /dev/sda1
mdadm: /dev/sda1 has no superblock - assembly aborted[/B]


Now I don't know what to try next, any help would be greatly appreciated. Thanks!

---

### Post by btkramer on 2014-02-21
okay, so after rebooting, and determining what drive goes where in what order, I thought I would try creating the array again in a degraded state. so I ran:

**sudo mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=4 /dev/sde1 missing /dev/sdd1 /dev/sdc1**

but I get: 
[B]
mdadm: super1.x cannot open /dev/sdd1: Device or resource busy
mdadm: /dev/sdd1 is not suitable for this array.
mdadm: super1.x cannot open /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 is not suitable for this array.
mdadm: create aborted[/B]

I was reading that possibly dmraid has a hold of these drives? can I get it to release them or stop them somehow? /dev/md0 is stopped

any help?

---

### Post by btkramer on 2014-02-23
can't anyone tell me how to stop or release these drives?

---

