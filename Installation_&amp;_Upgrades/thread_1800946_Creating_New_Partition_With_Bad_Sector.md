---
title: "Creating New Partition With Bad Sector"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by Zerocool3001 on 2011-07-09
I've been trying to move a Wubi install of Ubuntu to a dedicated partition (which involved creating a new one from scratch). However, since the disk (which is ntfs) reports a bad sector, gparted wont scan or resize the NTFS partition. I manually resized it using ntfsresize with the --bad-sector option, but since gparted wont scan the disk with the bad sector it won't report the new size or free space. This means I can use it to create new ext4 and swap partitions on which to install Ubuntu.

I know that the typical response to bad sector error is to toss out the disk, but that isn't an option. Given that the disk reports only 3 bad sectors, I don't think it necessarily needs replacing. Is there a way for me to force gparted to scan the disk and free space, or is there another *safe* way to create the partitions I need and have them be recognized?

---

### Post by srs5694 on 2011-07-10
The three bad sectors you're seeing with utilities like GParted are probably just the tip of the iceberg. Most modern disks have firmware that detects and quietly remaps a certain number of bad sectors in such a way that utilities like GParted never see the problem. By the time they *do* start showing up in GParted, it means you've got many more bad sectors. Thus, your hardware problem is probably much worse than you understand.

To be sure, you can run a SMART utility, such as smartctl, GSmartControl, or Palimpsest Disk Utility. These tools will tell you how many bad sectors you've got; however, their output can be difficult to parse. Post the results here if you have any doubts.

If you've shrunk the filesystem with ntfsresize, you should be able to resize the partition containing it with fdisk or sfdisk. You've got to be *very* careful, though. Back up your partition table with sfdisk before you begin, as in "sudo sfdisk -d /dev/sda > parts.txt" and copy parts.txt to a removable disk. Edit one copy of parts.txt to reflect the changed filesystem size and write it back with "sudo sfdisk -f /dev/sda < parts.txt". If you're not sure of the exact size, make your new partition a bit larger than your largest estimate of what it should be and resize the filesystem again to fill the new partition size.

Note that if the disk is showing bad sectors, you must use the bad blocks check option when you create a new filesystem in any partition you create in the affected area of the disk. This is the -c option to mke2fs, for example. If you don't do this, you're likely to run into disk errors as you use the partition. In fact, this is a very real possibility even if you *do* scan for bad blocks, since your bad blocks are likely to increase over time.

Finally, you've already mentioned and dismissed what is, IMHO, the correct solution to this problem: Replace the bad hard disk. Bad drives sometimes last for months without deterioration, but they also sometimes deteriorate very rapidly and without further warning. If you can't currently afford a new hard disk, make it a priority to be able to do so. Even a used disk is likely to be more reliable than one with enough bad sectors to be showing up outside of a SMART utility. In a worst-case scenario, your disk could die completely at any moment. Reviewing your SMART data should give you a better idea of how concerned you should be, though. It could be it's not as bad as I fear -- or it could be the disk is about to fail catastrophically.

---

### Post by Zerocool3001 on 2011-07-10
Thanks for the quick response. While I agree with you about replacing the disk, I'm doing this for someone else so it isn't really up to me. The SMART utility bundled with the included Disk Utility was were I first noticed the issue. It reports three bad sectors and a bad allocation count (because of the bad sectors). Given that it was such a low count, I didn't think it was immediately fatal.

Perhaps the best thing at this point would be to recommend exercising the warranty since the computer is only two years old. I would be hard pressed to believe that disk failure is common at that mark for this type of laptop.

I'm just not sure I want to edit the volume information myself on someone else's machine.

---

### Post by srs5694 on 2011-07-11
If the problem only appears in SMART, then GParted and other partitioning tools shouldn't be complaining. It's conceivable you're misinterpreting some unrelated problem as being related to the SMART bad sector count. Since you've already used ntfsresize, though, it's probably best to do one of two things:


[list]
[*]Use ntfsresize again to resize back to the full partition size, try using GParted (or whatever other tool you were using), and if it complains, provide screen shots, console error messages, or other detailed information about the error. That might lead to a better diagnosis of the problem and from there a solution.
[*]Use fdisk or sfdisk, as I suggested earlier, to resize the partition, then create new partitions in the freed space. This will leave the question of what caused the original error message unanswered, but you'll probably get a usable disk out of it.
[/list]


As to the bad sectors, I personally would be concerned even over three successfully remapped sectors; but some people aren't. At the very least, I'd keep an eye on the drive. If the error count increases, then it's certainly time to replace it.

---

### Post by Zerocool3001 on 2011-07-17
The problem actually appears in both SMART and gparted. I'll try and send some screen shots to make sure.

---

