---
title: "Shreded first 1.5 seconds of 2TB HD"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by kid1000002000 on 2011-03-09
Yes, you read it right, I made a horrible error!  Go figure that this would happen as I was just about to begin backing up the drive.  Any flames are welcome against me, provided you offer me *help* at the same time!

I was trying to recall a terminal command and accidentally hit enter to a previously issued "shred."  /dev/sdc was now attached to a drive I DID NOT want shredded, and I quickly realized the error and pulled the power to the machine.  Unfortunately, shred issued long enough (~1.5 seconds) before I had the machine powered off.

I KNOW the data on my 2TB drive is still there.  All that was corrupted was a very tiny piece of the drive.  I had 2 partitions in the following order: 750gb and ~1Tb.

My question is, will standard disk recovery options like testdisk be able to recover the majority of my data?

---

### Post by sanderd17 on 2011-03-09
yes, standard recovery tools will be able to recover the non-shredded part.

For the shredded part, you should ask help from the FBI :-P

---

### Post by oldfred on 2011-03-09
I do not know how shred works, but would expect it just to start at the beginning, but that is where the most important data is. There are backup super blocks and testdisk may be able to rebuild a partition table so you can directly read the second partition. You will have to use photorec for the first then.
Did you document the start & ends of your partitions anywhere? If so you can manually recreate partition table either fdisk or sfdisk. (Why I include a new copy of bootinfo script with every backup as it has lots of config data).

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by kid1000002000 on 2011-03-09
Thanks for the replies.  To clarify what you have said in your posts, do I have a chance at recovering the data in the first partition without photorec?  I would prefer not to use it so that I can recover more of my files.

---

### Post by oldfred on 2011-03-09
Until you try I do not know. But shred does it job.

I used photorec to recover some data. I had saved a text file many times into a larger partition. It recovered every version and some extra parts. I am not sure if I ever found the last saved version, but between backups and lots of work reviewing the recovered files I managed to get most of my file back.

---

### Post by kid1000002000 on 2011-03-12
reformatted and moved on with life.
for those who read this:

testdisk did not work
photorec worked
any attempt to rebuild partitions did not work

---

### Post by srs5694 on 2011-03-12
FWIW, the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) partitioning scheme stores a backup of all its important data at the end of the disk, along with the main set of data at the beginning of the disk, in order to help with exactly this sort of situation. If the disk had used GPT, it would have been possible to recover the partition table. The data *within* the partitions are another matter, though. Chances are you'd lose at least some data in the first partition on the disk, and if you used a single-partition layout, that could make recovering any files from the disk difficult. If, though, you split root (/) and /home, you might well have been able to rescue at least one of them.

Although the backup data make for a pretty minor advantage of GPT overall, in situations like this, it becomes an extremely major advantage. Fortunately, your type of situation is rare. In any event, because of this and other minor advantages, and one somewhat bigger one (the elimination of the distinction between primary, extended, and logical partitions), I recommend using GPT on Linux-only installations. Unfortunately, Windows won't boot from GPT on BIOS-based computers, so GPT may not be an option on a dual-boot computer.

---

### Post by kid1000002000 on 2011-03-12
I use the PC as a file server.  Sounds interesting...

---

