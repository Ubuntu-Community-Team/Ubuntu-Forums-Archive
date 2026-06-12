---
title: "RAID 0  DM - HD crashed and now what?"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by Camicia on 2010-04-06
Hi,
We have 4 HDs on our server. One of them broke last night. I could see a message on the server and after restarting the S.M.A.R.T. on the BIOS was recognizing one HD as bad.

After removing the failing HD, the server is now up and running. I also replaced it with a new HD of the same type but I didn't format or did any operation on it.

Now I had a few:  "SparesMissing event on /dev/md0:XXXX" on my account mail.

I have a problem: **I do not remember how I configured the HDs**. During the installation I had a few problems and I change a few times what I wanted to do.
I am sure I had at least a RAID0 with 2 disks but I could have put all the 4 disk in the RAID having 2 disks as spare drives **or** I may have created another volume for the other 2....

How do I find out what is going on? 

dmraid return: No raid disks
```
$ sudo dmraid -ay -vvv -d
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
no raid disks
WARN: unlocking /var/lock/dmraid/.lock
```Configuration:
```

$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=71a457fa:70ab9003:1d78346d:de02ee25
   spares=1

# This file was auto-generated on Fri, 06 Nov 2009 22:26:49 -0800
# by mkconf $Id$

``````
$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Nov  5 19:23:42 2009
     Raid Level : raid1
     Array Size : 488383936 (465.76 GiB 500.11 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr  6 20:19:25 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 71a457fa:70ab9003:1d78346d:de02ee25
         Events : 0.2104009

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

```MountManager seems to report that sda and sdb belong to linux_raid_member.
However there is no mount point.

Questions:
1-How do I find how the disk were and are configured?
2-How can I find what was on the disk that died? I identified the physical disk but was it a spare drive or the spare one? I suspect it was the spare ... but I am not sure.
3-What do I need to do now to be sure that the mirroring is working OK? (considering that there is a spare drive). Do I need to use a command to let ubuntu mirror the drive on the new one? If it was the spare one how do I insert back to the RAID volume?
4-What do I need to do now that I got the replacement and it is physically connected? 
5-What is an utility that can show me easily how the disks are configured and eventually makes a change.

Thank you ion advance
-Chris

---

### Post by Camicia on 2010-04-12
Can anybody give me a quick suggestion on what to do about this?

---

