---
title: "GParted Partition Resize Interrupted"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by Wug on 2013-02-09
OK, so this is basically worst case scenario: I was resizing and moving a large partition (Of course, I don't have a backup. please don't remind me) and during the actual partition copy my laptop locked up (HDD led stopped, no response to any stimulus) and had to be rebooted.

The operation in progress was moving an NTFS partition with a size of about 350GB to the LEFT by a few hundred GB.  It was about 95GB in.

Here's a picture (approximate) of the layout of the disk before and after the move.  The current layout looks like the "after", but the copy did not complete successfully.  Gparted correctly reports that the partition is all fscked up, and I know better than to try to mount it.  

[IMG]http://i.imgur.com/8NXRLmZ.png[/IMG]

So, assuming gparted isn't bat-**** insane, and based on both assumption and the progress of the operation, that gparted first moves the partition leftward to its desired location and then expands it rightward until it fills the requested space.  Since the operation was interrupted early on in the MOVING process, I think it's a fair assumption that the entire partition still exists more or less unscathed at its original location (not enough data had been copied to overwrite the beginning of the partition).

I'm currently using testdisk (recommended in another thread) to see if I can locate the correct beginning of the partition, but I suspect it is not going to work (it's most of the way through and has not found it yet).  I have not yet tried gparted's "Attempt Data Rescue" mode yet.

Is there a utility I can use to search for the original, correct beginning of the partition and to update the partition table entries correspondingly?

I also can't boot windows.  It's kind of on the partition.  Any alternatives to using chkdsk?

---

### Post by oldfred on 2013-02-09
Not sure if testdisk will find old start, but since some data was copied old partition will be corrupt, especially if data copied was the file information or MFT master file table. 

Photorec which is part of testdisk may find your files but it is slow and you have to have another drive with enough room for all the found data. It will also find deleted files, bits of files if they look complete and possibly mixed files if a test file is next to another it may see it as one. It only find files by extension or type as without MFT there are no filenames.

       [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)


Some say Windows tools may work better for Windows.
       
 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)

---

### Post by Mark Phelps on 2013-02-09
In my long experience, Windows utilities are BEST at manipulating Windows filesystem partitions; Linux utilities, at manipulating Linux filesystem partitions.

You should download and burn the Minitool Partition Wizard Boot CD (from a Windows PC).  That is a free Windows partitioning utility that understands NTFS partitions.  I don't know if the FREE version has the option to recover partitions -- but you can try it and see.

If it doesn't, you could consider purchasing the retail version and using it.

Once-click partition restoration would be a LOT less work than using RecoverMyFiles to get your files back (which will take HOURS) and then having to reinstall from scratch.

---

