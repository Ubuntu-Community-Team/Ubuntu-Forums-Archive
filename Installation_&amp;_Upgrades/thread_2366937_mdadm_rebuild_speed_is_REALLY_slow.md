---
title: "mdadm rebuild speed is REALLY slow"
date: 2017-07-24
forum: Installation &amp; Upgrades
---

### Post by sholmia on 2017-07-24
Hi,
I had to change failed hard drive, so my Raid 10 is in rebuild state now.
Until 60%, everything was OK.
Now, the speed is going between 10k to 1k /sec.
my /proc/sys/dev/raid/speed_limit_min is 100000
and /proc/sys/dev/raid/speed_limit_max is 500000
is there anything I can check?

---

### Post by TheFu on 2017-07-24
Reduce the load on the entire array while the rebuild is happening.
On a 4TB disk, my last rebuild took 26 hrs with ZERO load.

You can use blockdev to tune the disk cache and buffer parameters and hdparm to test the results.  There are guides on the internet - but it comes down to testing in a systematic way and changing the parameters until you find the values which work best for the specific hardware involved and workloads.

$ sudo /sbin/blockdev --setra 8196 /dev/sdZ
$ sudo hdparm -tT /dev/sdZ

Redhat recommends increasing it in 4M increments until you find the fastest result up to 32M in size.
Each different controller and disk model will have different optimal settings, IME.  Build a grid for the disks and different sizes, plan the test scenarios, then run them in a recordable way.

You can also tune the chunk sizes for the mdadm array, but that has to happen at creation time. Probably too late now. [https://wiki.mikejung.biz/Software_RAID](https://wiki.mikejung.biz/Software_RAID)

Hope this helps.

---

### Post by sholmia on 2017-07-25
So, I started the rebuild again, and the speed was really good, but when it gets to 65%, the speed drop to 13k/sec
 [=============>.......]  recovery = 65.0% (1270330688/1953382912) finish=69661.2min speed=321K/sec


and then drops to 100k so it's very very slow


```
mdadm -D:
/dev/md0:
        Version : 1.2
  Creation Time : Tue Apr 12 16:19:22 2016
     Raid Level : raid10
     Array Size : 21487212032 (20491.80 GiB 22002.91 GB)
  Used Dev Size : 1953382912 (1862.89 GiB 2000.26 GB)
   Raid Devices : 22
  Total Devices : 20
    Persistence : Superblock is persistent


    Update Time : Tue Jul 25 03:36:14 2017
          State : active, degraded, recovering
 Active Devices : 19
Working Devices : 20
 Failed Devices : 0
  Spare Devices : 1


         Layout : near=2
     Chunk Size : 512K


 Rebuild Status : 65% complete


           UUID : 12ec260e:98e29218:c957740e:0e958366
         Events : 286335


    Number   Major   Minor   RaidDevice State
      23       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
      26       8       48        2      active sync   /dev/sdd
       3       8       64        3      active sync   /dev/sde
       4       8       80        4      active sync   /dev/sdf
      24       8       96        5      active sync   /dev/sdg
       6       8      112        6      active sync   /dev/sdh
       7       8      128        7      active sync   /dev/sdi
      27       8      144        8      spare rebuilding   /dev/sdj
       9       8      160        9      active sync   /dev/sdk
      10       0        0       10      removed
      28       8      224       11      active sync   /dev/sdo
      12       8      192       12      active sync   /dev/sdm
      13       8      208       13      active sync   /dev/sdn
      29       8      176       14      active sync   /dev/sdl
      15       8      240       15      active sync   /dev/sdp
      16      65        0       16      active sync   /dev/sdq
      17      65       16       17      active sync   /dev/sdr
      18       0        0       18      removed
      25      65       32       19      active sync   /dev/sds
      22      65       48       20      active sync   /dev/sdt
      21      65       64       21      active sync   /dev/sdu


iostat:

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.04    0.00    3.55    0.65    0.00   95.77


Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               2.19         2.53        13.97     208171    1148024
sdd             120.77     23774.34         0.02 1953385432       1842
sdg             107.20     23774.31         0.02 1953383084       1346
sdk              80.29     15907.68         0.02 1307032012       1254
sdj              31.29         0.00     15907.65        140 1307029925
sdt             107.25     23774.33         0.02 1953385088       1834
sds               0.01         0.02         0.02       1828       1722
sdl             120.82     23774.34         0.02 1953385296       1354
sdo               0.01         0.03         0.02       2256       1362
sde              97.87     23774.31         0.02 1953383084       1842
sdp              98.04     23774.31         0.02 1953383084       1354
sdc              97.84     23774.31         0.02 1953383292       1950
sdm              98.01     23774.33         0.02 1953384852       1298
sdi              97.96     23774.31         0.02 1953383088       1266
sdn              98.07     23774.31         0.02 1953383084       1298
sdh              97.93     23774.33         0.02 1953384992       1266
sdq              98.11     23774.34         0.02 1953385336       1342
sdf              97.94     23774.34         0.02 1953385240       1346
sdr             101.13     23774.31         0.02 1953383084       1342
sdb             107.15     23774.37         0.02 1953387965       1950
sdu              98.13     23774.31         0.02 1953383084       1834
md0               0.12         0.31         0.19      25185      15316
sdv               0.00         0.00         0.00         44          0
sdw               0.00         0.00         0.00         28          0


```
[FONT=verdana]atop: [https://i.imgur.com/uMIpP4e.png](https://i.imgur.com/uMIpP4e.png)[/FONT]
[FONT=verdana][https://i.imgur.com/58k5cfA.png](https://i.imgur.com/58k5cfA.png)[/FONT]

---

### Post by wildmanne39 on 2017-07-25
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

