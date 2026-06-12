---
title: "installer raid sizing doubts"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by jholmes on 2007-08-12
Hi. I'm trying to install Fawn on software Raid1 (2 new exact same 500GB SATA drives), as per these instructions
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

When installing I set /home as ext3 with 1% blocks reserved for superuser (down from 5%) on a 488GB device. After, I check MDADM and somehow lost 34GB and even more in DF!

Maybe I'm missing something obvious - any ideas? Thanks.


jah@autopsy-turvy:~$ df -h / /home
Filesystem            Size Used Avail Use% Mounted on
/dev/md0              9.3G  2.4G  6.5G  27% /
/dev/md1              448G  205M  443G   1% /home


jah@autopsy-turvy:~$ cat /proc/mdstat
Personalities : [raid1] 
md2 : active raid1 sdb3[0] sdc3[1]
      1959808 blocks [2/2] [UU]
      
md1 : active raid1 sdb2[0] sdc2[1]
      476560128 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[0] sdc1[1]
      9863808 blocks [2/2] [UU]
      
unused devices: <none>


jah@autopsy-turvy:~$ sudo mdadm --misc --query --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Sun Aug 12 16:14:55 2007
     Raid Level : raid1
     Array Size : 476560128 (454.48 GiB 488.00 GB)
    Device Size : 476560128 (454.48 GiB 488.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Aug 12 20:53:11 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 7ff8b7b2:30e45637:7d2d15a5:39e8ff79
         Events : 0.16

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8       34        1      active sync   /dev/sdc2

---

