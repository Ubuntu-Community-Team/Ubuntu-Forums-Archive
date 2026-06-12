---
title: "ubuntu 10.04 install sets up partition table incorrectly gparted"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by harrismh777 on 2011-05-23
Greetings,
I have installed HP g6 notebook from live-cd with 10.04 LTS across multiple partitions, only to find that the partition table is not setup correctly.

I place the following mount points on separate partitions:
/boot
/
swap
(extended)
/usr
/opt
/tmp
/var
/home
/usr/local
/local

The partitioner (gparted?) created the partitions with overlapping beginning and ending cylinders!!!   example:

/dev/sda1     1    82     xxxxxxxx
/dev/sda2    82   274     xxxxxxxx     <====this is bad !

   the (82) overlap will lead to corruption!

All of my partitions ended up this way with the last and first cylinders overlapped !   Also,   /dev/sda4   disappeared from the partition table.

/dev/sda5 ended up as extended, and /dev/sda3 ended up as the first logical partition instead of the third physical partition. 

Also three of my partitions report in fdisk as 'does not end on cylinder boundary'  with overlapping first and last cylinders.

This caused many thousands of megs to be lost from the disk... not lost,... just not used !

To get this machine installed I booted from the cd, used fdisk to partition the drive, then installed from the live cd using the existing partitions.  This worked.

Whatever ubuntu is using to partition the drive is badly broken. The program does not give the user the option of specifying cylinders, just size in megabytes.

It is clear that ubuntu expects the user to install the entire system in one partition.  Multiple partitions is normal and expected by the linux community. One partition does not suffice.

This brings up one more little baby problem with ureadahead... it expects the pack file to be on /var on the same partition as /  !   My /var is on a separate partition, so the pack file cannot be found on boot-up.  I had to disable ureadahead to get rid of the messages on boot.



kind regards,
m harris

---

### Post by Hedgehog1 on 2011-05-23
M. Harris,

If you create your partition manually before you start the install, you can indeed follow the drive geometry by using whole cylinders.

[IMG]http://img197.imageshack.us/img197/4629/pgartedcyliners.png[/IMG]

Also - because your current layout is in megabyte rather than cylinders, the cylinder number repeating is not really an error, it just means the geometry is not 'ideal by the old rules'.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-23
As to your particular issue: Don't use so many partitions unless there is a real need.

For a desktop situation, these three get the job done:

[B]'/' (root)
'/home'
'SWAP'[/B]

Anything more without a real need is just wasting disk space and going to cause you grief (like the seperate '/var' issue). Even folks who have a separate '/boot' often run out of space or go nuts if they have to reinstall grub.


**The Hedge**

:KS

p.s. /dev/sda4 did not disappear - you made /dev/sda3 your extended partition to the end of the drive and lost the ability to make a forth primary partition (/dev/sda4) untill/unless you open mode space for it.  This is normal for MBR partitioned hard drives.

---

### Post by oldfred on 2011-05-23
Your partitions may not be overlapping. You have to use this to see the detail without rounding.
```

sudo fdisk -lu
```

Unless doing a server you do not need all the partitions:
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

