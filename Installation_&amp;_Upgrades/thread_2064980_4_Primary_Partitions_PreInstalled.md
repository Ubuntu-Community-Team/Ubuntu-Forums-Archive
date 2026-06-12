---
title: "4 Primary Partitions PreInstalled"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by karat on 2012-09-30
My new laptop came with 4 primary partitions already installed:

* 200 MB system info (partially filled)
* Windows Main Partition (C:)
* Windows Backup Partition (D:)
* 20G OEM Partition that Windows can't touch and thinks is 100% empty.

Now, the problem is that you can have at most 4 partitions with MBR:

[http://www.linuxbsdos.com/2011/09/18/guide-to-disks-and-disk-partitions-in-linux/](http://www.linuxbsdos.com/2011/09/18/guide-to-disks-and-disk-partitions-in-linux/)

The question is what do I do about this?  I was hoping the installer would have a solution, but it doesn't.  How safe is it for me to overwrite one of these partitions?  Is it possible to convernt from MBR to something like GPT?  Other suggestions?

---

### Post by darkod on 2012-09-30
There should be some type of recovery software installed. Open it and there should be an option to create a set of recovery DVDs from the recovery partition.
After that it's safe to delete the 20GB recovery partition. This option is also good because you can use those 20GB.

You will still have to shrink the partition next to those 20GB in case you want more space for ubuntu. Use windows Disk Management for that.

That should create a joined unallocated space, leave it as unallocated and the ubuntu installer will use it.

When shrinking, be careful which partition you shrink so that the unallocated space is created together. Otherwise it may create two separate spaces separated by an existing partition, in which case you can't really use all of it.

---

### Post by karat on 2012-09-30
> **darkod said:**
> There should be some type of recovery software installed. Open it and there should be an option to create a set of recovery DVDs from the recovery partition.
After that it's safe to delete the 20GB recovery partition. This option is also good because you can use those 20GB.

You will still have to shrink the partition next to those 20GB in case you want more space for ubuntu. Use windows Disk Management for that.

That should create a joined unallocated space, leave it as unallocated and the ubuntu installer will use it.

When shrinking, be careful which partition you shrink so that the unallocated space is created together. Otherwise it may create two separate spaces separated by an existing partition, in which case you can't really use all of it.

Which partition do you think is safe to reclaim -- the backup partition on D: or the 20G OEM partition?  If I delete both, I get contiguous space.

---

### Post by darkod on 2012-09-30
As I said, after creating the set of DVDs you can delete the 20GB recovery partition.
You can also shrink the D: partition, if it's next to it, to create unallocated space with the size you want for ubuntu. No need to delete D: completely, just shrink it enough so that it gives you the space for ubuntu you want.

Deleting only one partition is enough.

---

### Post by karat on 2012-09-30
> **darkod said:**
> As I said, after creating the set of DVDs you can delete the 20GB recovery partition.
You can also shrink the D: partition, if it's next to it, to create unallocated space with the size you want for ubuntu. No need to delete D: completely, just shrink it enough so that it gives you the space for ubuntu you want.

Deleting only one partition is enough.

Er, the 20GB partition is empty.  D: is the recovery partition.  I shrank C:, so there is space between the first 2 and last 2 partitions.

Maybe I can boot the Ubuntu install disc to delete the OEM partition (windows can't touch it), then I can create another partition after the first 2, then copy D: onto it, then delete d: ?

Or is there a way to "move" a partition?

---

### Post by oldfred on 2012-09-30
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.

You can move partitions, but NTFS partitions often do not like that. You have to at least run chkdsk on them afterwards. They have partition info in the PBR - partition boot sector that has to match the partition table. If NTFS using Windows tools is preferred.

If you want Windows tools:
EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

For Linux partitions use gparted.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by darkod on 2012-10-01
Hmm, recovery partition usually don't show in Computer, so when you said it shows up as D: I thought that wouldn't be the recovery one.

You might check what is on the 20GB partition from ubuntu live mode, it should be able to read it better. That way you can see if it's really empty or not. Don't trust windows since if it's marked Hidden for windows, I think it can't read it.

If you are sure D: is the recovery, delete that one after making the DVDs.

If you want further details, you can also boot the ubuntu cd in live mode, open terminal and post the output of:
```
sudo fdisk -l (small L)
sudo parted -l (small L)
```

---

### Post by karat on 2012-10-01
> **darkod said:**
> Hmm, recovery partition usually don't show in Computer, so when you said it shows up as D: I thought that wouldn't be the recovery one.

You might check what is on the 20GB partition from ubuntu live mode, it should be able to read it better. That way you can see if it's really empty or not. Don't trust windows since if it's marked Hidden for windows, I think it can't read it.

If you are sure D: is the recovery, delete that one after making the DVDs.

If you want further details, you can also boot the ubuntu cd in live mode, open terminal and post the output of:
```
sudo fdisk -l (small L)
sudo parted -l (small L)
```

Yes, the hidden partition did have data on it.  I ended up copying the data from d: to a directory and deleting the partition to make room for a fourth.

---

