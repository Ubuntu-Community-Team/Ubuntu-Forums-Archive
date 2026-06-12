---
title: "Madam Raid Degraded after grow"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by Gaute91 on 2012-06-03
Hello!
I have a Mdadm raid 5 with 4 1 TB disks. I recently added 2 more, one active and the other one as a spare. While growing, the computer suddenly shuts down (seems to be a clean shutdown). When i booted it up again, it stopped at a black screen, but the drives was working very hard, so I assumed that it was continuing the grow. After a couple of hours it stopped working, and i resetted the machine. The raid seems to work fine now, but every time i reboot the machine i get an error while booting, says "Raid Degraded want to use (y/n)" or something like that. This is a server, so I do not like to have this show up every time.
Is there something wrong with my array? Or is it maybe some way I can avoid this error?

Thanks, Gaute

---

### Post by darkod on 2012-06-03
Did you check what
cat /proc/mdstat

says?

---

### Post by Gaute91 on 2012-06-03
The /proc/mdstat seems fine:
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdg[4] sdc[2] sdd[3] sdb[1] sdf[0] sda[5](S)
      3907049984 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]

unused devices: <none>
```

here is my /etc/mdadm/mdadm.conf:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=5 UUID=d5b4480b:cdfca6e5:bd9f1658:0a1d2015 spares=1

# This file was auto-generated on Sun, 03 Jun 2012 00:28:27 +0200
# by mkconf $Id$

```

Everything seems fine to me?

---

### Post by darkod on 2012-06-03
I don't think it can be the issue, but why do you have the DEVICE line commented out in mdadm.conf?

I don't notice anything wrong either, but I'm not a big raid expert.

What about

sudo mdadm --detail /dev/md0

---

