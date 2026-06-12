---
title: "Complete Data Loss During Install"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by candyman9999 on 2008-10-03
Dear friends,

I had two hard drives in my PC - 160 GB (Win XP fully working with no data) and 250 GB (only data).

The 250 GB was further partitioned into three drives - 100 GB NTFS, 50 GB FAT-32 and another 100 GB NTFS.

During Ubuntu install, I accidently installed it on the 250 GB drive containingt all my data.

I see the following now:-

(a) I cannot boot from the 250 GB drive where I installed Ubuntu.

(b) I loaded Win XP back on the 160 GB drive and checked through "disk management" where the 250 GB drive is listed as "Dynamic unreadable".

I had my life's work on the 250 GB drive.

I will be most grateful if someone can help me with a step-by-step guide to restore my data.

Thanks and Regards,
Candyman

---

### Post by hwttdz on 2008-11-09
Edit: Actually now I read what you did.  I thought you had installed on a partition other than the dynamic partition.  I'm sorry but I don't think your odds are as good if you installed on top of your files.

---

### Post by Mark Phelps on 2008-11-10
Do you have XP back running now? Or are you still running Ubuntu?

You probably know that reformatting doesn't actually wipe the files, it just write new partition tables to the drive.  So, basically, the data is left intact.  That's the good news.

The bad news is that the Ubuntu installation most certainly overwrote SOME of the data, which is now, simply not recoverable.

The best way, in my experience, to recover the data would be to boot from a CD and run a utility that is written to do that.  There are several commercial data recovery products available, of which I've used GetDataBack, which works quite well.  However, they used to sell two separate versions, one for FAT 32 volumes, the other for NTFS volumes.  So, unless they have combined these in one product, you would need to buy both.

Another approach, if you want to try it, would be to use a partitioning product, and if you remember the size and sequence of the partitions, simply repartition your drive back to what it was.  It's not likely to work unless you know exactly the size and sequence of the original partitions.

---

### Post by Otustelija on 2008-11-10
1) Don't boot into Ubuntu anymore to avoid overwriting more files.

2) Boot into a live linux to inspect the drive - is it all one big partition etc.

3) Try file recovery software. There are some free ones - use Google.

You may need to repartition the disk into FAT and NTFS partitions for recovery programs to work. That shouldn't remove further files, but don't do it before you are sure you need to.

---

### Post by psusi on 2008-11-10
Insert backup media and restore.

In the event that you do not have backups, print this out and follow the directions:

[http://www.pdffun.com/antistress.html](http://www.pdffun.com/antistress.html)

;)

---

### Post by Carl Hamlin on 2008-11-10
The value of regular backups is so rarely a lesson learned the easy way. You have my condolences - I picked up the backup habit in a similar fashion.

---

