---
title: "mdadm: Nested Raid 5 starts degraded."
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by DannyW on 2007-05-12
I am wanting to set up a raid 5 array with 4 disks I have.
1x 200GB /dev/sdd1
1x 300GB /dev/sdb1
2x 500GB /dev/sda1 and /dev/sdc1

200GB + 300GB = raid 0 /dev/md0

/dev/md0 + /dev/sda1 + /dev/sdc1 = raid 5 /dev/md1

The kubuntu alternate install cd would not allow me to set up nested raid (would not allow me to use an existing raid disk as a new raid disk in another raid array) so I had to drop to the console and do this manually.

The raid 0 is simple, had no problems with this.

When I created the raid 5 array, it was created degraded and rebuilding, which is normal according to mdadm's man page.
> When creating a RAID5 array, mdadm will automatically create a degraded array with an extra spare drive. This is because building the spare into a degraded array is in general faster than resyncing the parity on a non-degraded, but not clean, array. This feature can be over-ridden with the --force option.
After a couple of hours when this had finished rebuilding both raid arrays were fine. And so with the help of mdadm --detail --scan --verbose I added this to mdadm.conf.
```
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=2ef71727:a367450b:4f12a4b2:e95043a1
   devices=/dev/sdb1,/dev/sdd1
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=4c4b144b:ae4d69bc:355a5a07:0f3721ab
   devices=/dev/sda1,/dev/sdc1,/dev/md0
```

When I rebooted the raid5 array is again degraded, with /dev/md0 removed.

Could this be a problem I have created by using a nested raid array?

To fix this problem I have to execute mdadm --manage /dev/md1 --add /dev/md0 (off the top of my head), and this re-adds the raid 0 device md0 and rebuilds it, taking another couple of hours. This is not ideal. Maybe it is because md1 is being created before md0. Is there any way of checking this?

I would appreciate any help at all.
Thank you.

```
danny@danny-desktop:~$ cat /proc/mdstat
Personalities : [raid0] [raid6] [raid5] [raid4]
md0 : active raid0 sdb1[0] sdd1[1]
      492191232 blocks 64k chunks

md1 : active raid5 sda1[0] sdc1[1]
      976767872 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]

unused devices: <none>
danny@danny-desktop:~$ cat /etc/mdadm/mdadm.conf
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

DEVICE /dev/sdb1 /dev/sdd1 /dev/sda1 /dev/sdc1/ /dev/md0

# definitions of existing MD arrays
#ARRAY /dev/md1 level=raid5 num-devices=3 UUID=4c4b144b:ae4d69bc:355a5a07:0f3721ab
#ARRAY /dev/md0 level=raid0 num-devices=2 UUID=2ef71727:a367450b:4f12a4b2:e95043a1
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=2ef71727:a367450b:4f12a4b2:e95043a1
   devices=/dev/sdb1,/dev/sdd1
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=4c4b144b:ae4d69bc:355a5a07:0f3721ab
   devices=/dev/sda1,/dev/sdc1,/dev/md0


# This file was auto-generated on Fri, 11 May 2007 18:08:52 +0100
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $

danny@danny-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /dev/sda3
UUID=99873af1-7d82-476c-975e-7165fedb7cee       /               ext3            defaults,errors=remount-ro      0       1
# /dev/sda1
UUID=56703a2b-449e-4c73-b937-41e5de341a0d       /boot           ext3            defaults                        0       2
#/dev/mapper/vghome-lvhome
#UUID=afb1f00e-a7ef-48ce-b136-082d4b82276a
/dev/mapper/vghome-lvhome                       /home           reiserfs        defaults,nodev,nosuid           0       2
# /dev/sda2
UUID=801702de-257d-481b-b0de-9ad2108893da       none            swap            sw                              0       0
/dev/scd0                                       /media/cdrom0   udf,iso9660     user,noauto                     0       0
proc                                            /proc           proc            defaults                        0       0
danny@danny-desktop:~$ sudo mdadm --misc -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu May 10 12:59:25 2007
     Raid Level : raid0
     Array Size : 492191232 (469.39 GiB 504.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat May 12 12:13:32 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 2ef71727:a367450b:4f12a4b2:e95043a1
         Events : 0.11

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1
danny@danny-desktop:~$ sudo mdadm --misc -D /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Thu May 10 20:33:15 2007
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
    Device Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat May 12 12:30:06 2007
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 4c4b144b:ae4d69bc:355a5a07:0f3721ab (local to host danny-desktop)
         Events : 0.1628

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed
danny@danny-desktop:~$ sudo mdadm --detail --scan --verbose
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=4c4b144b:ae4d69bc:355a5a07:0f3721ab
   devices=/dev/sda1,/dev/sdc1
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=2ef71727:a367450b:4f12a4b2:e95043a1
   devices=/dev/sdb1,/dev/sdd1

```

---

### Post by kidders on 2007-05-13
Hi there,

The level of detail in your post is great. :-) I'm surprised you haven't gotten any responses yet!

There is one more possibility:

Your problem could be the result of the order Ubuntu is dismounting your devices in, at shutdown. Consider, for example, what might happen if md0 were shut down before md1. No matter how the arrays were re-assembed, md1 would always be degraded.

On my system, for instance, I have an array that uses ATA over Ethernet to access one of its components. Since networking is normally deactivated before block devices are dismounted, you would expect such an array to always start degraded.

If I were you, I would temporarily force Ubuntu _not_ to automatically assemble the arrays at boot time, and do it once myself ... just to confirm what's really going on. Depending on whether you can successfully reassemble your layered RAID manually, you should be able to figure out which suggestion (yours or mine) is correct.

It's worth noting that, while nesting software RAID devices may be relatively uncommon, it is a perfectly acceptable (and sometimes essential) thing to do ... so it *should* work flawlessly. If you find yourself having to do an unreasonable amount of tweaking to get your arrays to disassemble and reassemble in the right order, you might like to consider filing a bug report. The other thing that strikes me is that surely Ubuntu's installer should either make it clear that it does not support setting up layered RAID, or let you do it. I don't like the idea that the only reason you know it can't do it is because you tried it!

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by DannyW on 2007-05-15
Hello, thanks for the response!

I have solved this problem for now.

It seems the UUID's of the device's belonging to my raid5 array weren't all the same.

I followed this howto:
[http://ubuntuforums.org/showthread.php?t=410136](http://ubuntuforums.org/showthread.php?t=410136)

Note, however, if anyone has the same problem as me, you must stop not only the raid5 array but also the raid0 array within the raid5, and then reassemble them both.

When only recreating the raid5 array (md1) the UUID's again decided they didn't want to stay the same.

I now have no problems.

```
$ cat /proc/mdstat
Personalities : [raid0] [raid6] [raid5] [raid4]
md0 : active raid0 sdb1[0] sdd1[1]
      492191232 blocks 64k chunks

md1 : active raid5 sda1[0] md0[2] sdc1[1]
      976767872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>
```

---

