---
title: "Recreate RAID Array in new installation"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by starNIX on 2005-07-16
So I had a Raid array working on my old gentoo install and I now installed gentoo

So how do I get my raid array back without losing the data on it.

I use software raid and I have 3 disks

/dev/sda1
/dev/sdb1
/dev/sdc1

Now I dont have my original raidtab file and I am not sure exactly what parity algorithm I used.

mdadm --examine /dev/sda1 shows this

Code:

/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.01
           UUID : fa3848cc:c6a7bbc9:3ae0049b:72f6d5aa
  Creation Time : Tue Jul 12 03:27:06 2005
     Raid Level : raid5
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Jul 12 04:26:51 2005
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 9e9e4e26 - correct
         Events : 0.113020

         Layout : right-asymmetric
     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1



I believe that the last time I had to rebuild it in gentoo I used Webmin but how do I get webmin to work in Ubuntu?  I hear there is some problem with needing root enabled before installing it.  What do I need to do?

So this is the new raidtab I have come up with.

Code:

raiddev /dev/md0
raid-level 5
nr-raid-disks 3
nr-spare-disks 0
persistent-superblock 1
chunk-size 4
parity-algorithm right-symmetric
device /dev/sda1
raid-disk 0
device /dev/sdb1
raid-disk 1
device /dev/sdc1
raid-disk 2


Does this look right?

So what command do I have to run to get it to rebuild it?

mkraid?

I tried "mkraid /dev/md0" and I got:
Code:

handling MD device /dev/md0
analyzing super-block
disk 0: /dev/sda1, 17928508kB, raid superblock at 17928384kB
/dev/sda1 appears to be already part of a raid array -- use -f to
force the destruction of the old superblock
mkraid: aborted.
(In addition to the above messages, see the syslog and /proc/mdstat as well
 for potential clues.)


Please help. I really can't lose this data.

---

### Post by alastair on 2005-07-16
Use "raidstart" to start the array i.e.

/sbin/raidstart /dev/md0

Then try and mount.

I am surprised you are using raidtools and not mdadm.

---

### Post by starNIX on 2005-07-16
How do I use mdadm?  And what's the difference?



Damn,  raidstart worked.  I for some reason thought it was more involved than that.  How do I get it to start automatically on boot?

---

### Post by alastair on 2005-07-16
The reason I am surprised is :

a) raidtools is deprecated for a while, and distributions are stopping using it
b) mdadm appears the standard RAID config option in Ubuntu

The main difference is probably that mdadm is actively maintained and supported - do some Google research. This is what Ubuntu will use if you install on RAID for instance - and what the init scripts look for - at least 5.04.

Anyway - glad you've got it working.

---

