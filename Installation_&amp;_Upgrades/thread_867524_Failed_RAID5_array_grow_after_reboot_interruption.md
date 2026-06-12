---
title: "Failed RAID5 array grow after reboot interruption"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by zac_haryy on 2008-07-22
I used mdadm to create a RAID 5 array awhile ago (6 months) and I have 5 tb hard drives in it and wanted to grow it to 8 tb hard drives. It stated that it was going to take it 3 days to do, which is perfectly fine. It was going fine and then after about 2 days my electricity went out. So this completely interrupted the grow process obviously. So I started searching on google for a solution. I came up with this link: [thread]("http://www.issociate.de/board/post/486857/Failed_RAID5_array_grow_after_reboot_interruption;_mdadm:_Failed_to_restore_critical_section_for_res.html"). At the sixth post it explains how he was able to correct his problem. All he had to do was get his version of mdadm to v2.6.4. The version of mdadm that I am usuing is v2.6.2. Well his problem is a little different. I can login into the desktop environment so I have easy access to everything. I don't want to loose any data that I have on the RAID 5 because it is very important and I should have backed it up but didn't. So anyways, I could try and update mdadm to v2.6.4 but not exactly sure how and didn't want to loose anything if i just tried to update it. I am pretty new with linux so please be easy with me and explain stuff in detail (it would just help me out a lot :) ). When i run this command ```
mdadm --examine /dev/sdi1
``` this is what I get:

```
harold@server:~$ sudo mdadm --examine /dev/sdi1
/dev/sdi1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

  Reshape pos'n : 4642814400 (4427.73 GiB 4754.24 GB)
  Delta Devices : 3 (5->8)

    Update Time : Thu Jul 17 15:01:47 2008
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 3d26208 - correct
         Events : 0.441232

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8      129        4      active sync   /dev/sdi1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       97        2      active sync   /dev/sdg1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8      129        4      active sync   /dev/sdi1
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8       33        6      active sync   /dev/sdc1
   7     7       8       17        7      active sync   /dev/sdb1

```

Any help at all would be great! Thanks!

-haryy

---

### Post by zac_haryy on 2008-07-23
Here is what I get with some commands:

```
harold@server:~$ sudo mdadm --assemble /dev/md0
mdadm: no devices found for /dev/md0
```
```
harold@server:~$ sudo mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.
```
```
harold@server:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
```
```
harold@server:~$ sudo mdadm --E /dev/md0
mdadm: unrecognized option `--E'
```

---

### Post by zac_haryy on 2008-07-23
Can I just upgrade mdadm and not loose anything or will it affect it?

---

### Post by zac_haryy on 2008-07-23
According to this thread [HTML]http://www.linuxquestions.org/questions/linux-server-73/raid-5-mdadm-grow-interrupted-what-to-do-next-602671/[/HTML] he has said that he was able to assemble his array back together but never said if he lost his data or not. I was just wondering if anybody knows if this would. I really don't want to try it if not sure because I don't wanna loose data :(

---

### Post by zac_haryy on 2008-07-27
Any help at all would be great! I am not the greatest with linux and can't find anywhere what I should do.

---

