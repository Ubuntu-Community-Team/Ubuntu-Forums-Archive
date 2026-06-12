---
title: "Cloning a disk with Clonezilla: puzzles, problems?"
date: 2019-08-09
forum: Installation &amp; Upgrades
---

### Post by orthoducks on 2019-08-09
I need help interpreting the results of some disk operations.

My system runs from a dual-boot disk with Ubuntu 16.04 and Windows 7. I'm trying to clone the disk.

I ran Clonezilla. It reported an error copying /dev/sda7. When it was done I displayed partclone.log as the error message directed. It only contained information about a different partition. I think Clonezilla overwrites the log file each time it processes a partition.

I tested the clone disk. It booted successfully to both Ubuntu and Windows. When I examined the disk with parted, it said that the format of /dev/sda7 was "unknown."

I booted the original disk. Parted said /dev/sda7 is an NTFS partition, which is correct. I ran fsck on it. fsck ran for only fraction of a second (this is a 20 GB partition with at least several thousand files) and displayed this:

fsck from util-linux 2.27.1

I did some research but I can't figure out what that means. Some of the sources I found say that fsck should display a single number: 0=OK, 1=errors corrected, etc. One source answered a person who got the message "fsck from util-linux 2.20.1" and told them that their disk was fine, but didn't explain what the numbers mean.

The disk clone is supposed to be my backup of all my installed software. I'm uncomfortable about the unexplained error message from Clonezilla and the cryptic results from fsck, even though the clone disk "seems to work fine." Can anyone help me understand what happened, and what problems, if any, warrant concern?

---

### Post by sudodus on 2019-08-09
- Did you check that the target drive is at least as big as the source drive? If the target is smaller than the source, the last partition will be truncated (and damaged).

- Did you check (in Windows), that the problematic NTFS file system is healthy (in the source drive as well as in the target drive (the cloned copy)? There might be logical (software) damages or physical damages (hardware). It might be possible that the tool in Windows can repair the damage(s). (Use Windows tools to check and repair Windows file systems and linux tools to check and repair linux file systems; fsck is not the best tool for NTFS.)

---

### Post by orthoducks on 2019-09-14
The two drives are exactly the same size. (I always clone to same-size drives.)

I did not try to check-disk the problem partition. It's been about a week since I worked on the problem and I won't be able to revisit it until Monday night at the soonest, but as I recall,I reformatted the partition in Windows with a third-party partition management tool, and had no more trouble.

Today I had a similar problem with the Windows partition on another disk, on another computer. (I installed Windows and Ubuntu, and in Windows I installed Firefox and a couple of tools, and defined some simple batch files. Then I tried to clone the disk, and Clonezilla said no.) Check-disk in Windows solved the problem.

The two incidents together seem to point to a recurrent problem in the Windows installer's disk formatting.

But at this point I'm mainly concerned about fsck: how to understand what it tells me about the disk, if "fsck from util-linux 2.27.1" actually tells me anything about the disk.

---

### Post by CatKiller on 2019-09-14
> **orthoducks said:**
> But at this point I'm mainly concerned about fsck: how to understand what it tells me about the disk, if "fsck from util-linux 2.27.1" actually tells me anything about the disk.

It doesn't. That's the version number. The utility is called fsck. The package that provides that utility is called util-linux. The version of that package that you have installed on your system is 2.27.1.

As sudodus said, Windows tools are best for mucking about with Windows filesystems.

---

