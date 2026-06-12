---
title: "Ubuntu 11.04 Install question related to Partitions"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by martinchito203 on 2011-08-13
Hi all.
I'm a new user into the Ubuntu world searching for help while trying to install Ubuntu 11.04 in a multi partitioned Drive.

I've loaded GParted (loading through "try" option) and it shows the following:

```

Partition   - File System - Size      - Used      - Unused   - Flags
/dev/sda1   - ntfs        - 100MiB    - 33.59MiB  - 66.41MiB - boot
/dev/sda2   - ntfs        - 156.15GiB - 97.31GiB  - 58.85GiB -
/dev/sda3   - ntfs        - 309.51GiB - 231.10GiB - 78.41GiB -
unallocated - unallocated - 1.02MiB   -           -          -
```

The computer has a hard drive with Windows 7 installed in a C: drive (sda2). Windows has created a system partition (sda1) of 100Mb.
It has another partition of about 310Gb with data (sda3).

My question is the following: How I can whipe Windows 7 and install Ubuntu in the new empty space (sda+sda2) without loosing the data in the sda3 partition?
I´ve to create the Ubuntu partitions manually? How?
I'm lost here :(

Thanks in advance for your help and comments.

Best regards!

---

### Post by Rhizoid on 2011-08-13
First step - backup to an external medium.  Something like clonezilla if  you're used to Windows software and need a GUI solution or use dd or  tar if you're confident with the command line - this way, if you're not  happy with the results you can restore and start over.

Next step - use gparted to remove sda2.  Apply the changes by clicking the green tick.

Now create a new primary partition with size 20GB, format it to ext4

Now create a new extended partition using the remaining space on the  disk.  Inside the extended partition, create a new ext4 partition of  10GB to use as Linux swap and then a further partition using the  remaining space and format it to ext4.

Apply the changes again using the green tick.

Your partition table should look something like:

```

Partition   - File System - Size      - Used      - Unused   - Flags
/dev/sda1   - ntfs         - 100MiB     - 33.59MiB  - 66.41MiB - boot
/dev/sda2   - ext4        - 20.15GiB  -  0.00GiB  -  20.15GiB -
/dev/sda5   - extended - 130.0GiB  -  ---      -  ---
  /dev/sda6 - ext4        - 120.00GiB -  0.00GiB  - 120.00GiB
  /dev/sda7 - linux-swap  -  10.00GiB -  ---      -  ---
/dev/sda3   - ntfs        - 309.51GiB - 231.10GiB - 78.41GiB - unallocated - unallocated - 1.02MiB   -           -          -

```Note - the actual partition names may differ - note them carefully for use in the next step.

Install Ubuntu by running the link on the desktop and when the option re  partitioning appears choose the manual config, use the 20GB partition  as ext4 with the mount point /, the 130GB partition as ext4 with the  mount point /home and the 10GB partition as swap.

Once installed you need to edit the /etc/fstab file to automatically  mount the 309GB NTFS partition, I'd suggest the mount point /mnt/data,  but anywhere you want to mount it will be fine as long as you know  where.

Sing out if any of that needs clarifying.

Cheese!

---

### Post by Brenden.Rea on 2011-08-13
First I would back up the data you would like to keep to an external hard drive, which is always good practice for switching OS' or even upgrading your distro.

secondly, I would format both your /dev/sda1 +/dev/sda2 (remember that if you format the partition your system is currently running off of, it would really screw up your computer)

once /sda1 + /sda2 they should show up with your unallocated 1.02 Mib giving you 156.16 Gib(approx)

after this I would change the filesystem format of your unallocated data to Fat32 (so you can install Linux) ([http://ubuntuforums.org/archive/index.php/t-154095.html](http://ubuntuforums.org/archive/index.php/t-154095.html)) 

then boot from your CD or USB

Follow the installation steps and voila! you should have a completely annihilated windows from your computer as well as installed your flavor of Linux as your primary! 

Good luck!



P.S. follow Rhizoids response, I am fairly beginner for most of this... 
P.P.S. Rhizoid, would my response work? why/ why not

---

### Post by Rhizoid on 2011-08-14
I wouldn't use FAT32, ext4 is far more advanced.  FAT32 is somewhat outdated, even Microsoft has dropped it as a default filesystem.  

Removing both sda1 and sda2 isn't a bad idea, it just doesn't gain you much space as sda1 is only 100MB.

I would definitely recommend using the manual partition setup during this install, it's not that difficult to follow and as long as you've already made the changes you want to the partitions, there's no need to format anything during the install, which cuts down the margin for error when there's stuff you want to keep.

The reason for a separate root and home partition is to simplify re-installation at a later date.  You can reinstall your OS, or even change distro entirely, without losing settings and data for installed applications - e.g. mail, browser cache, desktop preferences, wine config etc. etc.

Hope that helps,

---

