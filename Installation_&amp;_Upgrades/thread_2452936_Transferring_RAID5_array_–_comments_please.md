---
title: "Transferring RAID5 array – comments please"
date: 2020-10-30
forum: Installation &amp; Upgrades
---

### Post by helen314 on 2020-10-30
I am in a process of temporary transferring RAID5 array &#8211; from USB stick to USB drive.  
 I have successfully added copy of current  array /dev/sdkx  partitions  as /dev/sdex  
 using mdadm &#8211;add  &#8230;.  
 

 
 I have experienced an error advising to &#8220;backup critical ...&#8221;  
 Unfortunately my barely limping Ubuntu 16.04.7 froze so I did not get the actual copy of the message.  
 
```

```After reboot I checked the array :  

 

 
 ```


root@f-SATA:/home/f# mdadm --detail /dev/md42

 /dev/md42:
         Version : 1.2
   Creation Time : Thu Oct 15 09:50:58 2020
      Raid Level : raid5
      Array Size : 5564416 (5.31 GiB 5.70 GB)
   Used Dev Size : 2782208 (2.65 GiB 2.85 GB)
    Raid Devices : 8
   Total Devices : 8
     Persistence : Superblock is persistent
 

 
     Update Time : Fri Oct 30 13:58:49 2020
           State : clean, reshaping  
  Active Devices : 8
 Working Devices : 8
  Failed Devices : 0
   Spare Devices : 0
 

 
          Layout : left-symmetricState : clean, reshaping  
      Chunk Size : 512K
 

 
  Reshape Status : 32% complete
   Delta Devices : 5, (3->8)
 

 
            Name : a-SATA:42
            UUID : fbe4babd:b3c28449:66d4881d:46391ff4
          Events : 286
 

 
     Number   Major   Minor   RaidDevice State
        0       8      161        0      active sync   /dev/sdk1
        1       8      162        1      active sync   /dev/sdk2
        4       8      164        2      active sync   /dev/sdk4
        8     259        6        3      active sync   /dev/sde22
        7     259        5        4      active sync   /dev/sde21
        6     259        4        5      active sync   /dev/sde20
        3       8      163        6      active sync   /dev/sdk3
        5       8      165        7      active sync   /dev/sdk5




```

 

root@f-SATA:/home/f#  
 

 
 Please note its &#8220;state&#8221; :
 State : clean, reshaping  
 It is going to take some time.  
 

 
 Can I make the following assumptions ?
 

 
 1. **After &#8220;reshaping &#8220; is done &#8211; can I physically remove sdk ?**

    It is USB  memory stick. But it probably will remain as a (what type?  inactive ?? ) of device in md42 array .
I can live with that. 

 2. **Would it be prudent to &#8220;remove&#8221;  sdkx  using mdadm software instead?.**

   It should not take much of real time is my best guess.

---

### Post by helen314 on 2020-10-31
Update

As an experiment, I did , after copying the array contents to another , plain partition, physically REMOVED the USB drive.
After reboot, reinserted th USB stick. 
Did not expect the array to be functional, but this got me puzzled. 
At one point the entire array was gone.

Here is a series of commands of strange responses and still not functioning array.


```

f@f-SATA:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid5 sde11[3] sde17[4](S) sde4[0] sde5[1] sde18[5](S)
      204668928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md42 : inactive sde21[7](S) sde22[8](S) sde20[6](S) sdk2[1](S) sdk4[4](S) sdk5[5](S) sdk3[3](S) sdk1[0](S)
      22798336 blocks super 1.2
       
md20 : active raid5 sdf22[3] sdf20[0] sdf21[1]
      204668928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md3 : active raid5 sdf12[0] sdf13[1] sdf14[3]
      204668928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md1 : active raid5 sde9[3] sde19[5] sdd9[4]
      204668928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md0 : inactive sda3[0](S) sdc4[1](S)
      204668928 blocks super 1.2
       
unused devices: <none>
f@f-SATA:~$ sudo mdadm --run /dev/md42
[sudo] password for f: 
mdadm: failed to start array /dev/md/42: Input/output error

f@f-SATA:~$ sudo mdadm --assemble --force /dev/md42
mdadm: Found some drive for an array that is already active: /dev/md/42
mdadm: giving up.

f@f-SATA:~$ sudo mdadm --detail /dev/md42
/dev/md42:
        Version : 1.2
  Creation Time : Thu Oct 15 09:50:58 2020
     Raid Level : raid5
  Used Dev Size : 2782208 (2.65 GiB 2.85 GB)
   Raid Devices : 8
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Fri Oct 30 18:44:01 2020
          State : active, FAILED, Not Started 
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : a-SATA:42
           UUID : fbe4babd:b3c28449:66d4881d:46391ff4
         Events : 465

    Number   Major   Minor   RaidDevice State
       0       8      161        0      active sync   /dev/sdk1
       1       8      162        1      active sync   /dev/sdk2
       4       8      164        2      active sync   /dev/sdk4
       8     259        6        3      active sync   /dev/sde22
       7     259        5        4      active sync   /dev/sde21
       6     259        4        5      active sync   /dev/sde20
      12       0        0       12      removed        this is /dev/sdk3  what "removed it"? 
      14       0        0       14      removed        this is /dev/sdk5 
f@f-SATA:~$ 


```

So I a have "  State : active, FAILED, Not Started" which is "   mdadm: Found some drive for an array that is already active: /dev/md/42" 
and  "mdadm: giving up. "

Any suggestion what to TRY next ?

---

### Post by helen314 on 2020-10-31
YAA
Yet another addendum 





```

f@f-SATA://etc/mdadm$ sudo mdadm --assemble  --scan 
mdadm: ignoring /dev/sde22 as it reports /dev/sdk4 as failed
mdadm: ignoring /dev/sde21 as it reports /dev/sdk4 as failed
mdadm: ignoring /dev/sde20 as it reports /dev/sdk4 as failed
mdadm: /dev/md/42 assembled from 3 drives - not enough to start the array.
mdadm: /dev/md/00 is already in use.
f@f-SATA://etc/mdadm$ 



```


Array is assembled but it was initially created with 8 members.
Question:
**Is it possible to change # of devices in an array after it has been created?**
 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

---

