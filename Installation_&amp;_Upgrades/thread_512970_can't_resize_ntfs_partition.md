---
title: "can't resize ntfs partition"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by Lary Grant on 2007-07-29
I'm trying to install Feisty as a dual-boot option onto a Windows machine which has the whole hard disk allocated to an NTFS partition.  When I get to part of the install were I can edit partitions, I tell it to resize the NTFS partition and I get:

Resize operation failure

An error ocurred while writing the changes to the storage devices.  The resize operation is aborted.

I tried increasing the "new size" of the NTFS partition to be much larger than the "space used" and I still got the error.

What should I do to get past this?

---

### Post by merlinus on 2007-07-30
What version of windows are you running?  If vista, then use its disk management tool to resize the drive.

Also, beforehand, delete temp files, etc., and defrag several times.  You can also set your paging file to zero, and then reset it after resizing the partition.  It usually occupies a large chunk near the end, and makes resizing difficult.

-merlin

---

### Post by splintercellguy on 2007-07-30
And of course make sure to backup before performing the resize.

---

### Post by Lary Grant on 2007-07-30
It's XP, not Vista.

OK, I will try the suggestions, but it's hard to work in my friend's Windows, because it is so virus-infested.  (This is why they are "resorting" to letting me put Ubuntu on their machine).

---

### Post by rbmorse on 2007-07-30
Cleaning up those viruses before resizing partitions would be a very good idea. Many of the better (tm) infections live in track 0 or do nonstandard things to disc geometry and may interfere with a partition editing tool.

---

### Post by Lary Grant on 2007-07-30
I understand, but we've already put quite a lot of time into trying to clean up the viruses.

---

### Post by merlinus on 2007-07-30
Best bet is to reformat the entire drive.  This will get rid of the virus problems, and any other lurking nasties.

-merlin

---

### Post by Lary Grant on 2007-07-30
True, but it will also get rid of their data files and also a path back to the "status quo ante" (i.e. the situation as it was before I got involved), which, for obvious reasons, I would like to maintain :)

---

### Post by adasuper on 2007-08-01
When i was resizing my hard drive partition i used Power Quest's Partition magic in windows to resize the  partition, before installing Ubuntu. It did not give me any problems, try it and see. Don't forget to back up your files first!

---

### Post by Lary Grant on 2007-08-01
How much did you have to pay for that?

---

### Post by merlinus on 2007-08-01
I fail to understand why you want to pay money when gparted live cd is open source and free!!!

And probably lots better to boot.

-merlin

---

### Post by Pumalite on 2007-08-01
Hey Merli; you forgot to say: 'pardon the pun'

---

### Post by merlinus on 2007-08-01
Yeah, I missed it myself, the first time.

:)

-merlin

---

### Post by Lary Grant on 2007-08-02
I think the Ubuntu install also uses gparted and that's what is not working!

---

### Post by merlinus on 2007-08-02
The ubuntu live cd uses an older version of gparted.  gparted live cd is the latest, and has improved resizing and other updated features that clearly work better.

-merlin

---

