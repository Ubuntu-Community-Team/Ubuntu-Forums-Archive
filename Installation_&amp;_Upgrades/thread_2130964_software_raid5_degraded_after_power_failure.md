---
title: "software raid5 degraded after power failure"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by btkramer on 2013-03-31
so, i 'm pretty new to ubuntu. i set up a home media server running 12.04 server, and setup a software raid5 array for it, following a tutorial. last night, there was a power failure, and when i tried to reboot i got a message saying the raid array was degraded. i booted anyways, and all my data is still there. i doubt that the drive actually failed. more likely it has become corrupted. although i do have a spare drive to replace it if needed.

how do i rebuild the array? i have found quite a few relevant posts, and have a basic idea how to proceed, but i could use some advice/direction.

what i have found out so far is that the array is mdp01, consisting of 4 drives, sda1-sdd1. the state of the array is listed as clean, degraded, and it seems that the drive sdb1 is the one with the problem, with its state listed as removed. 

so, from what i can gather, i need to stop the array, and add the drive which has been removed back to the array and resync, but i can't seem to find out exactly how to do that.

thanks!

---

### Post by darkod on 2013-03-31
Post the outputs of these commands:
```
cat /proc/mdstat
sudo mdadm --examine /dev/sd[abcd]1
```

That should give us little more details.

---

### Post by btkramer on 2013-03-31
brian@Ubuntu-Server:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd1[3] sda1[0] sdc1[2]
      5860535808 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [U_UU]
      
unused devices: <none>
brian@Ubuntu-Server:~$ ^C
brian@Ubuntu-Server:~$ sudo mdadm --examine /dev/sd[abcd]1
[sudo] password for brian: 
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
     Array Size : 11721071616 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b7cf63a5:d093e89a:bfa44323:b9f4cdf5

    Update Time : Sun Mar 31 18:50:48 2013
       Checksum : 6ef26026 - correct
         Events : 28467

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.AA ('A' == active, '.' == missing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ecabf5:ea889c14:26169875:c4bfdf8c
           Name : Ubuntu-NAS:0
  Creation Time : Fri Oct  5 21:32:19 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 11721071616 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 4dc1f6de:a9f820e5:a7ca17c5:dc3f3eac

    Update Time : Mon Mar 18 02:31:02 2013
       Checksum : 4af2e24c - correct
         Events : 64

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
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
     Array Size : 11721071616 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 9fde527f:4238b936:5f360b53:c6dac84a

    Update Time : Sun Mar 31 18:50:48 2013
       Checksum : 69748b46 - correct
         Events : 28467

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : A.AA ('A' == active, '.' == missing)
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
     Array Size : 11721071616 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ba87cbc8:a3eb76b0:39aeb5e4:076872d7

    Update Time : Sun Mar 31 18:50:48 2013
       Checksum : 4afeecc8 - correct
         Events : 28467

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : A.AA ('A' == active, '.' == missing)

---

### Post by darkod on 2013-03-31
Yeah, it looks like only sdb1 was dropped. I would zero the superblock on sdb1 to delete the old mdadm info, and add it to md0 again as new member:
```
sudo mdadm --zero-superblock /dev/sdb1
sudo mdadm --add /dev/md0 /dev/sdb1
```

After that let it sync fully, you can watch the sync process with cat /proc/mdstat. It might take a while.

After it's synced it should be fine.

---

### Post by btkramer on 2013-03-31
thanks! 

do i need to stop the array first?

---

### Post by darkod on 2013-03-31
You shouldn't need to. Adding a disk can be done while the array is working, that's the point.

Usually you only stop the array to grow or reshape it.

---

