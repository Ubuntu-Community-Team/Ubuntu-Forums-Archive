---
title: "&quot;Bad Primary Partition&quot; after g4u big drive to smaller one"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by questioningquestioner on 2010-09-05
Hi there... Perhaps this is a question for the people who make g4u (ghost for unix) but i thought that maybe some linux wizard would have the answer


I have recently ghosted, using g4u, an 80 gig drive to a 30 gig drive. The data size is about 15 gig so no problem there.

The system does work and it doing everything it should, except for some errors in dmsg log and also the following error when you run cfdisk:

/var/logs/dmesg
```

[   35.516431] attempt to access beyond end of device
[   35.516438] sda: rw=0, want=156296251, limit=60058656

```

cfdisk output
```

     FATAL ERROR: Bad primary partition 1: Partition ends after end-of-disk
                          Press any key to exit cfdisk

```

The thing is though, that the system works! all the services are running and live... And i have years worth of customizations in this machine. Has been running for several years, so i dont just want to reformat and reinstall.
Its hard to get linux the way you want it sometimes!


So my question is this, is there a way to fix my partition or somehow tell the machine what the current boundries <i>should</i> be?


Any help appreciated!

Ubuntu version is 8.04 LTS

---

### Post by srs5694 on 2010-09-06
Post the output of the following commands from the system booted using the smaller disk, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility:

```

sudo fdisk -l
df -h

```

My suspicion is that the disk partition and/or filesystem is too big for the device. This might allow the system to boot, but some of your data may be missing, and if not, the system could eventually try to write beyond the disk's capacity, which will lead to wackiness.

---

### Post by questioningquestioner on 2010-09-06
Ok

sudo fdisk -l
```

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d5b75c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2385    19157481   83  Linux
/dev/sda2            2386        9729    58990680    5  Extended
/dev/sda5            2386        2491      851413+  82  Linux swap / Solaris
/dev/sda6            2492        9729    58139203+  83  Linux


```

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G   12G  5.9G  67% /
varrun                506M  212K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   48K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm

```

But i think what i will do, since its an option at this point, is just swap physically the original disk. it was not dying, it was just a bit slower so i was swaping it.

anyways, i will just wait till i have some time to deploy 10 LTS and redeploy from scratch. takes a while but whatever at least its all clean.


I thought there was some way to fix it though, but perhaps not in a bit by bit transfer such as g4u does.


thanks anyways, unless you are just curious and want to solve it. I am sure its a problem that someone else may have at some point.

---

### Post by questioningquestioner on 2010-09-06
Perhaps the question should be restated as, How do you "ghost" a larger drive to a smaller one in linux?


Maybe thats easier to answer. Is it just using DD or what?

---

### Post by srs5694 on 2010-09-06
Your fdisk output suggests that the drive was truncated, not properly resized during the copy operation. Note that the drive is reported as having 3738 cylinders, but /dev/sda6 ends at cylinder 9729. That partition doesn't seem to be mounted, so it's not clear to me what it is, or if its filesystem might at least have been resized.

You might look into [Clonezilla](http://clonezilla.org) for whole-disk duplication and backup. I've never used it, though, and the Web page states that the target disk must be as large as or larger than the source disk, so I doubt if it would work for your specific case.

A more general technique, but one that requires more work on your part, is to use tar to copy the drive:


[list=1]
[*]Create partitions on the new disk that match those on the original, but resized for the new disk. Be sure each target partition is large enough to handle the files it will receive.
[*]Create filesystems on the target disk's partitions.
[*]Mount the target disk's partitions at convenient locations.
[*]For each partition to be backed up, use tar. For instance, to back up /home to /mnt/home, you'd type "cd /home; sudo tar cp --one-file-system --file - ./ | (cd /mnt/home; sudo tar xvf -)". Repeat this step for each filesystem partition. (There's no need to copy swap partitions.)
[*]In the backup of the root filesystem, edit etc/fstab to adjust the UUID numbers for the new disk. (Use blkid to get the new UUID values.)
[*]Unmount the backup disk.
[/list]


This process can be automated in a script designed for your particular set of partitions, if you like.

---

### Post by questioningquestioner on 2010-09-07
Thanks! At least i will know for next time.

---

