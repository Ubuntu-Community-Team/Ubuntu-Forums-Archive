---
title: "Install with /var and /home mounted to RAID disks"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by madhartigan on 2009-11-16
I'm using the server install disk for Ubuntu 9.10 and I'm installing on 5 different disks that have been wiped with zero's using Darik's Boot and Nuke QuickErase.

The five disks are the following:

1 74GB WD Raptor
2 1000GB WD Caviar 
3 320GB WD Caviar
4 320GB WD Caviar
5 1000GB WD Caviar

Using the install disk, I go to the manual option for partitioning.  I then create a new blank partition for all disks.  I then go into the Create RAID disks option.  I first create the RAID 0 disk using both 1TB disks (#2 and #5).  I then create a RAID 1 disk using both 320GB disks (#3 and #4).

I then "Finish" the RAID disk part of the partitioning and go back to the main partitioning menus and now select the RAID 0 array and I tell it to use the partition as an EXT4 filesystem with /home mounted to it.  Next, I select the RAID 1 array and tell the partitioner to use the partition as an EXT4 filesystem and mount /var to it.

I then create a new partition in the 74GB disk (#1) and then tell the partitioner to "Automatically partition the disk" to use it as my Linux OS disk.

When I boot into the system and type "sudo df -H" after logging in, this is what I get:

```

root@server1:/# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               71G   867M    66G   2% /
udev                   4.2G   246k   4.2G   1% /dev
none                   4.2G      0   4.2G   0% /dev/shm
none                   4.2G    37k   4.2G   1% /var/run
none                   4.2G      0   4.2G   0% /var/lock
none                   4.2G      0   4.2G   0% /lib/init/rw

```

I don't know why my RAID disks are not being mounted as I designated in the install, but I would really like it to work right because it's a PITA to use the LiveCD to move /var and then modify the fstab file to mount the disks properly.  The install should do it for me.

Any help with this is appreciated.

Thank you!!

---

### Post by b0b138 on 2009-11-16
Because after you've started the manual partitioning and made your striped set and your mirrored set, you're going back and telling it to do automatic partitioning on #1, which will undo what you just setup.

The only thing you need to do different is while you're still under manual partitioning, select #1 and mount it as /

---

### Post by madhartigan on 2009-11-17
Thank you b0b138!!

About 10 minutes after I typed that thread, I thought through the sequence and had the realization of what you recommended.  Hopefully this solved thread can at least assist someone who may make my same error in the future.

---

