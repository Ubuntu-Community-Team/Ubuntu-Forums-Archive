---
title: "Software RAID boot fails on 2.6.27-2"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jove on 2008-09-12
Well, I bit the bullet yesterday and upgraded from Hardy. I'm posting this from Intrepid, but there's a problem. I can't boot into 2.6.27-2 with my softraid setup. It's an ASUS P5N-E SLI MoBo, and the disks look like this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a86cbf3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   82  Linux swap / Solaris
/dev/sda2             244       30637   244139805   fd  Linux RAID autodetect
/dev/sda3   *       30638       60800   242284297+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a86cbf3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         243     1951866   82  Linux swap / Solaris
/dev/sdb2             244       30637   244139805   fd  Linux RAID autodetect
/dev/sdb3   *       30638       60800   242284297+   7  HPFS/NTFS

However, on boot I'm dropped into BusyBox with messages:

ALERT! /dev/md0 does not exist
and
md0 : inactive dm3[0](S)

At this point I thought I'd try "mdadm --assemble --scan" which does, in fact, activate md0 - but only with one of the two raid partitions active. If I try to mdadm --add the other one, I get "mdadm: Cannot open /dev/sda2: Device or resource busy"

I've checked initrd and both md and raid1 modules are included.

Note: booting into 2.6.24-21 (and other earlier kernels) works absolutely fine, so that's what I'm running at the moment.

Any clues / hints?

Cheers,

Alan.

---

### Post by Jove on 2008-09-12
Update: same problem on 2.6.27-3, unfortunately.

---

### Post by Jove on 2008-09-12
Some more info:

Booting into 2.6.27-3 recovery mode gives more details on the console. Both sda and sdb disks (and partitions thereof) are detected ok, but just prior to being dropped into BusyBox there's a load of messages like this:

md: md0 stopped
md: bind<dm-2>
md: md0 stopped
md: unbind<dm-2>
md: export_rdev(dm-2)
md: bind<dm-2>
md: md0 stopped
md: unbind<dm-2>
md: export_rdev(dm-2)
md: bind<dm-2>
md: md0 stopped
md: unbind<dm-2>
md: export_rdev(dm-2)
md: bind<dm-2>
Done.
** WARNING: There appears to be one or more degraded RAID devices **

(However, both drives are fine, as I can boot earlier kernels without problems).

Then, I'm offered an option to start the degraded device. If I choose "Y", md0 starts but with only one drive active (similar to the result I got from mdadm --assemble --scan)

Some kind of race condition on drive detection, maybe?

---

### Post by Nullack on 2008-09-12
Please see the contributing to intrepid link in my sig

---

### Post by Jove on 2008-09-12
Roger wilco! I assume you're suggesting I file this as a bug, yeah? However, the page you referred me to says, "Whenever you encounter a reproducible malfunction in Intrepid, file a bug report. It's a good idea to start a thread in the development forum before submitting your report, to discuss it with others who may have experienced it, to make sure it's genuine."

So, I'll file it as a bug then? Can't find any other references...

---

### Post by Jove on 2008-09-15
Some more info which hopefully will help in tracking this down. I'm still being dropped to an BusyBox shell on boot, with the option to start the degraded array. If I answer "Y", the system boots successfully (even Compiz works) but with only one disk of the 2 disk mirror active:

$ cat /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 dm-3[1]
      244139712 blocks [2/1] [_U]

Now, I thought I'd just have to mdadm --add the remaining partition, BUT:

$ mdadm --add /dev/md0 /dev/sdb2
mdadm: /dev/md0 does not appear to be an md device

~$ mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.

Each of the individual RAID partitions seem to be ok:

~$ mdadm --examine /dev/sda2
/dev/sda2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 38cddd7c:4d8e4943:01d1eea6:dbfc78ed
  Creation Time : Fri Jun 29 10:30:57 2007
     Raid Level : raid1
  Used Dev Size : 244139712 (232.83 GiB 250.00 GB)
     Array Size : 244139712 (232.83 GiB 250.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0

    Update Time : Mon Sep 15 13:47:47 2008
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
       Checksum : ab366c25 - correct
         Events : 3436

$ mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 38cddd7c:4d8e4943:01d1eea6:dbfc78ed
  Creation Time : Fri Jun 29 10:30:57 2007
     Raid Level : raid1
  Used Dev Size : 244139712 (232.83 GiB 250.00 GB)
     Array Size : 244139712 (232.83 GiB 250.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0

    Update Time : Mon Sep 15 13:47:48 2008
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
       Checksum : ab366c2a - correct
         Events : 3438

Still stumped here, I'm afraid. Help! :)

---

### Post by Jove on 2008-09-15
Interestingly, when I reboot back into 2.6.24-21, the output from /proc/mdstat looks different:

$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb2[1]
      244139712 blocks [2/1] [_U]
      
unused devices: <none>

Note it's saying that sdb2 is active now rather than dm-3 as it did on 2.6.27-3

---

### Post by Jove on 2008-09-15
Dozy twonk. I didn't sudo the mdadm --add command :( - will try this and report back.

---

### Post by Jove on 2008-09-15
Ok - I think I may be getting to the bottom of this. I *think* kernel 2.6.27 is picking up a FakeRAID mirror set up on my NVIDIA chipset motherboard. This is a change in behavior from previous kernels which didn't detect the NVIDIA mirror and instead I could use software raid on the two softraid partitions, sda2 and sdb2. Now, however, the kernel is picking up a dm device and  attempting to boot from that. Of course, as it's a RAID-1 mirror, the kernel sees it as only one device and complains as the original softraid mirror appears to have only one device rather than two.

Maybe if I disable fakeraid support until after boot then manually modprobe dm-mirror... ?

---

