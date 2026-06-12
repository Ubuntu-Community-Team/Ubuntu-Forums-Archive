---
title: "PLease help:Unable to mount a partition after extending with windows disk management"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by princehektor on 2011-03-20
Hi Friends,
             I am a beginner in ubuntu and only recently did i install Ubuntu 10.10 using Wubi. I am dual booting along with Windows 7 64bit. Before i got to know of Wubi, i created a free 20GB partition for installing linux. But since it was of no use , i decided to extend another partition adding this 20GB space. 
The problem now is that i am getting the following error while trying to access the partition.

"Error mounting: mount exited with exit code 12: Failed to read last sector (605949951): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?"


These are the results after running  sudo fdisk -l /dev/sda:

"Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76c4009c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          13      102400   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              13        6528    52326400   42  SFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            6528       42717   290694144   42  SFS

Please help me out in this.

---

### Post by Quackers on 2011-03-20
It seems that you may have fallen foul of Windows latest trick.
When you created a 20GB partition I presume you chose "primary"?
If so, it seems that you created a 5th primary partition. As your HDD almost certainly uses the mbr partitioning system (most do) that 5th primary partition was "illegal" and, as a result, Windows changed your existing 4 primary partitions to "dynamic disks". This is ok for Windows, but a disaster for any other operating system, as they cannot install on it.
If you really want another operating system installed on your pc you will need to re-install Windows.

---

### Post by ronparent on 2011-03-20
Or... possibly reduce your partition count to 3 or less with windows leaving unallocated space and then using the live cd to create an extended partition in the unallocated space. My memory is getting faint on this issue but I have inadvertently created more than four partitions in win7 and then undone it and used Ubuntu to create an extended out of unallocated.

---

### Post by Quackers on 2011-03-20
ronparent, does that change the SFS file system back? That would be good to know, though I haven't seen that mentioned before.

---

### Post by ronparent on 2011-03-20
I don't know?? I had created extra partitions in prep for Ubuntu before I realized that win7 was creating only 'primary' partition. I then deleted and left unallocated space and used Ubuntu to create an extended to install to. It worked!!! The only problem was that I was improvising on the spot and am not sure of the details. What's to lose?

---

### Post by Quackers on 2011-03-20
Interesting, thanks.

---

### Post by srs5694 on 2011-03-20
I've heard that at least a couple of third-party Windows partitioning tools ([Partition Wizard](http://www.partitionwizard.com/) and [EASEUS,](http://www.partition-tool.com/personal.htm) IIRC) can convert from Windows "dynamic disks" back to regular partitions. You could look into doing that.

One caution: Juggling partitions around at this level is inherently at least a little dangerous -- not as dangerous as moving partitions, but still a bit risky. An error can leave you with no way to access your filesystems, although they'll probably still be intact. (It'd be a bit like walking into an unfamiliar library where all the shelves are unlabelled. Even if you knew the call number for a book, it'd take you a while to find it.) Thus, I strongly recommend backing up all your important data before proceeding.

---

