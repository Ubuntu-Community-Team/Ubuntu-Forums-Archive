---
title: "Partitioning the Disk with Windows"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by kooia on 2010-03-13
Hi,
 
When you paratition the disk on windows, it leaves all your documents on it, right?
 
[IMG]http://www.askdrtech.com/solutions/image.axd?picture=2009%2F7%2Fdefrag4.jpg[/IMG]
 
There, there's 49% left. IF I set Ubuntu to 48% of the disk, would it destroy the files that are on the right 48% of the disk? Or, does it not matter if you defragment
 
That's not my hard drive deframenting, it's just one I found on the web. It's rather small at 4 GB.

---

### Post by thomas144 on 2010-03-13
I don't think that you would lose the last 48% of the disk when you partition your hard drive. But, you should back up your files before you install Ubuntu. If you have an external hard drive, there are ways to copy your entire hard drive to the external drive. I don't know much about this. When you parition a drive, there's always some risk. Another thing is that you shouldn't use almost all of your free space for Ubuntu. The Windows partition will be almost full, and Windows will give you warnings. You might not be able to run certain programs and do some other things. How big is your hard drive?

---

### Post by kooia on 2010-03-13
Yeah, I have a 300GB drive, so I'm not worried.  I was just giving an example, since our drive has information scattered all over it (even after we defragment it).
 
What about making a FAT32 area?  How do you do that?

---

### Post by efflandt on 2010-03-13
I am always apprehensive about letting something automatically format my drives based on possibly different criteria than what I might want.

Windows may have some files that are not movable, including virtual memory (similar to swap file).  So if you are going to resize Windows, it would be a good idea to temporarily disable virtual memory (reboot for that to take effect), then defrag your hard drive to move files lower on the disk.  Then you could use Gparted on the install CD to shrink Windows, and then tell the Ubuntu installation to use the unallocated space that you just freed up.  Later, you can re-enable virtual memory in Windows.

The first time I tried to make room for 64-bit WinXP beta and SuSE in 2004, I could only shrink my 200 GB drive by 24 GB (apparently I forgot to reboot after disabling virtual RAM).  So I created 12 GB partitions for each.  When I installed XP64 beta, even though I told it to use an existing partition, it totally messed up my partition table geometry, and I had to use fdisk expert mode from a Linux rescue CD to fix it based on partial information I could remember and trial and error.  Eventually I was successful with no data loss.

When I discovered Ubuntu and was going to remove the XP64 and old SuSE partitions to make more space to try 32 and 64 bit Ubuntu, I found that by correctly disabling virtual RAM (rebooting) and defragging the drive, I could have freed up well over 150 GB.  But I just created a couple of 32 GB partitions and swap (for now).

---

### Post by srs5694 on 2010-03-13
There are two data structures that are critical for this: Partitions and filesystems. Partitions are just contiguous chunks of hard disk space, defined in data structures stored in the first sector of the disk or in some other area defined by the partitioning system in use. Filesystems are much more complex, and they're defined by data structures stored throughout a single partition (or occasionally on an unpartitioned disk or in some other area, like inside a file).

Some disk utilities can resize a partition as well as the filesystem it contains. When such utilities encounter files or file fragments that fall outside of the target area for the partition, they move those files or file fragments. Once everything's been moved, they adjust the filesystem structures and then resize the partition.

Other disk utilities lack this ability. Usually, such tools lack a "resize" option, but I've seen one or two that do have such options; they just change the size of the partition without resizing the filesystem it contains. If you don't understand them, such tools can be extremely dangerous.

I *think* that the partitioning tools that come with Windows can do filesystem resizing, but I'm not positive of this.

---

### Post by Mark Phelps on 2010-03-14
> **kooia said:**
> Hi,
 
When you paratition the disk on windows, it leaves all your documents on it, right?
 


Don't understand your question ... 

A partition is a container for a filesystem.  If you reformat an existing partition, you effectively erase the files inside it because you wipe out the partition table.  You don't actuall wipe the file contents ... but that's a different discussion.

So, if you're asking if your documents remain intact if you repartition an existing disk, the answer is NO -- unless you shrink the existing partition first, and then just create a new, empty partition in the free space.

> There, there's 49% left. IF I set Ubuntu to 48% of the disk, would it destroy the files that are on the right 48% of the disk? Or, does it not matter if you defragment.

MS windows always needs some room for temp files, log files, etc.  Shrinking it too close to the existing used space runs the risk of rendering it then unbootable because it no longer has enough space to write its temp files.

BTW, defragmentation doesn't affect the AMOUNT of free space in a partition, just the physical arrangement of the file blocks.  What prevents partition shrinkage is the insistence of MS Windows in writing some system files near the end of the partition.  Unless the defrag operation moves them (and it usually does NOT), you're not going to be able to free up much space.

---

### Post by srs5694 on 2010-03-14
> **Mark Phelps said:**
> A partition is a container for a filesystem.  If you reformat an existing partition, you effectively erase the files inside it because you wipe out the partition table.  You don't actuall wipe the file contents ... but that's a different discussion.

I believe you mean "...you effectively erase the files inside it because you wipe out the *filesystem data structures*...", not "...wipe out the *partition table.*" (emphasis mine to highlight the change). "Formatting" (that is, creating a new filesystem on) a partition doesn't affect the partition table; it just affects the filesystem data structures.

> So, if you're asking if your documents remain intact if you repartition an existing disk, the answer is NO -- unless you shrink the existing partition first, and then just create a new, empty partition in the free space.

It's also possible to delete or otherwise change some, but not all, partitions on a disk. In that case, only the deleted or changed partitions' files will be affected.

---

