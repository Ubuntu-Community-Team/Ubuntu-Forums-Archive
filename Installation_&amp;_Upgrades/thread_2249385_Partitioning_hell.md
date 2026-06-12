---
title: "Partitioning hell"
date: 2014-10-21
forum: Installation &amp; Upgrades
---

### Post by f00dl3 on 2014-10-21
So I had a 500 GB HDD (and spare for monthly clones). I was going to upgrade to 3 TB drives but found that my motherboard BIOS does not support GPT as no matter what I did it locked up after checking for bootable media. 

I ended up buying 2x 2 TB drives and used CloneZilla to copy the data from the 500 GB drive to the 2 TB drive. After copying over the data, I resized the partitions.

This is where things got interesting - what I did was the following:

Deleted the "primary" Windows XP 10 GB partition
"Moved" the Extended partition to the front of the drive.
Deleted the 50 GB Windows NTFS "data" partition
Left the 4 GB Linux SWAP alone.
"Moved" and resized the Linux partition to the maximum I could (1.79 TB)

So when I had it all set up, and for a bit, it looked proper and booted fine... with the Ubuntu partition filling the majority of the space w/ Linux SWAP.

Problem is I (probably a big no-no) wanted to zero out the old 500 GB drive. I unmounted all of the partitions except the Linux Swap partition (as GParted would not let me do this) and started the dd -if /dev/zero -of /dev/sdX command... and the computer went blank shortly after. After a reboot, I powered back up, and all my data is fine and in tact, booted fine. Worked on it some more this morning, and now when I'm trying to clone the drive to the clone "standby" drive I'm getting some kind of weird data outside of partition error. I checked gparted - it shows the whole disk unallocated. Using sfdisk, I get the following:

astump@astump-EX58-UD4P:~$ sudo fdisk -l -u /dev/sda

Disk /dev/sda: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa50ea50e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           12288  3907027055  1953507384    f  W95 Ext'd (LBA)
/dev/sda5   *     9781248  3907026943  1948622848   83  Linux
/dev/sda6           14336     9779199     4882432   82  Linux swap / Solaris


astump@astump-EX58-UD4P:~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=    12288, size=3907014768, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=  9781248, size=3897245696, Id=83, bootable
/dev/sda6 : start=    14336, size=  9764864, Id=82


Since everything works fine, restoring from the 500 GB drive would be an option (as I have my changes to my database and other files backed up to external media)... but if there is a way to repair the partition table...

---

### Post by oldfred on 2014-10-21
I do not see the error. 
Partition table largest entry is less than drive.

But partitioning is not good for a new 4K drive. Would have been much better to have started from scratch.
And a few BIOS (mostly Intel)  require boot flag on a primary partition. Grub does not use boot flag, but Windows has to have it on a primary partition, so some BIOS expect Windows?

       [http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary](http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary)
Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

   First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

My system is from 2006 & 2009. It has worked with gpt partitioning since I installed 10.10 using a gpt drive so I could learn about gpt. I now only partition new drives with gpt. And since drive may get moved to a newer system I include an efi partition and a bios_grub partition so I could boot with BIOS or UEFI. 

XP did not work at all with gpt partitioned drives. Newer Windows only boots from gpt drives with UEFI but reads gpt data drives whether booting BIOS or UEFI without issue.

---

### Post by f00dl3 on 2014-10-22
Im biting this as a mistake either caused by a rogue dd command, or by deleting the primary partition and leaving only the extended. Mirring over, then will resize, keeping the 10gb XP partition for bootability purposes. And disconnect all but the drive I wish yo zero out next time, as that may have been the cause even though I was zeroing the other physical disk with all but swap unmounted (gparted wouldn't let me unmount swap on inactive disk for some reason.)

---

