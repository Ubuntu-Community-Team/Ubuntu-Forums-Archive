---
title: "Help, I broke my raid."
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by Popkinson on 2012-06-20
I'm not quite sure what happened, but the first disk of my Raid1 array disappeared. Here's what the array looks like now:

```
phil@rolf:~$ sudo mdadm --query --detail /dev/md*
mdadm: /dev/md does not appear to be an md device
/dev/md0:
        Version : 1.2
  Creation Time : Wed Feb 22 10:08:44 2012
     Raid Level : raid1
     Array Size : 974673784 (929.52 GiB 998.07 GB)
  Used Dev Size : 974673784 (929.52 GiB 998.07 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Wed Jun 20 15:22:13 2012
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : rolf:0  (local to host rolf)
           UUID : e0700ed2:fe77fff7:4e12d832:3a0a5ef4
         Events : 87862

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1

```

I assumed I could just add the missing second disk back in - there's nothing wrong with it. But this is what happens next:

```

phil@rolf:~$ sudo mdadm --add /dev/md0 /dev/sda1
mdadm: add new device failed for /dev/sda1 as 2: Invalid argument

```

I assume the clue lies in the 2. Shouldn't the disk be getting added as 0? I've tried various things but not had any success in getting /dev/sda1 back to its rightful place in the array.

Please explain this to me as you would to a small child. My expertise in Linux is very limited.

Thanks.

---

### Post by darkod on 2012-06-20
What is the output of:
cat /proc/mdstat

---

### Post by Popkinson on 2012-06-20
Sorry, meant to include that too:

```
phil@rolf:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1]
      974673784 blocks super 1.2 [2/1] [_U]
      
unused devices: <none>

```

---

### Post by darkod on 2012-06-20
Did you check if /dev/sda1 is still of type raid?

sudo parted /dev/sda print

EDIT PS: In general, it still looks fine since raid1 can work with one disk. In the worst case, if something went wrong on the superblock of /dev/sda you can zero the superblock and add the disk as if it was a new disk replacing a failed one.

---

### Post by Popkinson on 2012-06-20
It looks like this:
```
phil@rolf:~$ sudo parted /dev/sda print
Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  998GB   998GB   primary                boot, raid
 2      998GB   1000GB  2135MB  extended
 5      998GB   1000GB  2135MB  logical

phil@rolf:~$ 

```

...which is identical to the output for sdb.

---

### Post by darkod on 2012-06-20
You can try what the auto assemble will do:
```
sudo mdadm --assemble --scan
```

You can also check the content of /etc/mdadm/mdadm.conf to see if the md0 device is still containing two partitions.

---

### Post by Popkinson on 2012-06-20
Hmmm. This is what happens:

```
phil@rolf:~$ sudo mdadm --assemble --scan
mdadm: /dev/md/0 is already in use.

```

Presumably this is because I'm using the array (the system boots from it)

Here's what's in mdadm.conf:

```
 mdadm.conf
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
ARRAY /dev/md/0 metadata=1.2 UUID=e0700ed2:fe77fff7:4e12d832:3a0a5ef4 name=rolf$

# This file was auto-generated on Wed, 22 Feb 2012 10:19:42 +0000
# by mkconf $Id$


```

---

### Post by darkod on 2012-06-20
You can try to zero the superblock od sda1 to delete all raid data remains, and add it like a new disk (partition).

First make sure again in cat /proc/mdstat that the sdb1 is the active partition, to prevent deleting the superblock of the wrong device. When you have confirmed that sda1 is still the partition outside of the array, try something like:
```
sudo mdadm --zero-superblock /dev/sda1
sudo mdadm --manage /dev/md0 --add /dev/sda1
```

See if that makes it add it correctly. If it does, you can check the synchronization process progress with cat /proc/mdstat also.

---

### Post by Popkinson on 2012-06-20
```
phil@rolf:~$ sudo mdadm --zero-superblock /dev/sda1
mdadm: Couldn't open /dev/sda1 for write - not zeroing

```

It's still thwarting me. Sorry.

---

### Post by darkod on 2012-06-20
Almost looks like /dev/sda1 is mounted somewhere and it can't manipulate it.

Let me try to call some expert help. :)

---

### Post by rubylaser on 2012-06-20
What does the superblock metadata look like on each disk?

```
mdadm -E /dev/sd[ab]1
```

Also, what does the smart info look like for the disk that's fallen out of the array?
```
smartctl -a /dev/sda
```

You can see what's accessing the disk like this.
```
lsof | grep sda
```

Finally, if a disk was previously removed from an array, you would **--re-add** it to the array rather than --add it.  This will work if the metadata on the device reports that it is a member of the array, and the slot that it used is still vacant, then the device will be added back to the array in the same position. Unfortunately, without an intent bitmap, this will still require a resync.

---

### Post by Popkinson on 2012-06-20
Unusually for me, semi-random tinkering just fixed the problem.

I used gparted to delete the existing partitions on /dev/sda, then recreated them using

```
sudo sfdisk --force -d /dev/sdb | sudo sfdisk --force /dev/sda
```

--force seemed to be necessary because sfdisk otherwise complained about cylinder boundaries.

Then I formatted the two new partitions (again in gparted) to match those on /dev/sdb.

After that I was able to successfully use:

```
sudo mdadm --manage /dev/md0 --add /dev/sda1
```

Right now the raid is doing a recovery, so hopefully that's it.

Thanks for all your help, darkod (and rubylaser).

---

### Post by rubylaser on 2012-06-20
Sounds good, but you shouldn't have had to re-adjust the partitions with gparted (not that it will hurt anything), the sfdisk should make the two disks have exactly the same partition structure.  Post back and let us know how it turned out.

---

### Post by Popkinson on 2012-06-20
It worked out fine. sda1 is now back in the array and behaving as it should (at least according to cat /proc/mdstat)

While sfdisk created partitions of the correct size, gparted seemed to suggest that they were not formatted. Manually formatting to the correct filesystem seems to have solved my issue.

---

### Post by rubylaser on 2012-06-21
> **Popkinson said:**
> It worked out fine. sda1 is now back in the array and behaving as it should (at least according to cat /proc/mdstat)

While sfdisk created partitions of the correct size, gparted seemed to suggest that they were not formatted. Manually formatting to the correct filesystem seems to have solved my issue.

Oh, yes, you do need to apply a filesystem to the newly created partitions.  I usually just use mkfs for that, but glad you got it working :)

---

