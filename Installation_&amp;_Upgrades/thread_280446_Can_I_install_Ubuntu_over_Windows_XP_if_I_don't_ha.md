---
title: "Can I install Ubuntu over Windows XP if I don't have unpartitioned space? (Solved)"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by kernco on 2006-10-19
I have Windows XP on my laptop, and I want to dual-boot Ubuntu.  The entire hard drive is an NTFS partition right now, and I was wondering if Ubuntu can safely shrink that partition to make room for itself without any data loss?  I've heard in the past that disk partition tools that shrink existing partitions are unreliable in terms of preserving data.  Is this true?

---

### Post by bulldog on 2006-10-19
The best thing to do **before** you install is to backup important data.

Then run windows defrag several times to make sure  everything is neat and tiedy.

All done,you can install Ubuntu and let it install by itself.

---

### Post by aysiu on 2006-10-19
Yes, theoretically it can resize without data loss.

In practice, it works only about 99% of the time, which is fine for most people, but if your data is important to you, you have to account for that 1% chance and **back up your data**.

---

### Post by kernco on 2006-10-19
Here's another question.  I should probably just start a new thread:  For data I want to work with from both OSs (read and write), should I put it in the Windows NTFS partition, or should I use a Linux FS (I haven't looked, but I assume there are windows programs out there that allow use of ext or other filesystems?)

---

### Post by Ambimom on 2006-10-19
The answer is yes, but first....

There are three options when you install. The first one will erase everything on your hard drive, including windows.  Don't select that one.

The next will automatically partition your hard drive for dual boot.

The last option is a manual partition of your hard drive, but don't do this if you are a noob.

Do backup and defrag as recommended above. 

Whatever you do, Ubuntu will ask your permission before it installs permanently.  Just take it slow, read everything carefully, and if you're unsure, cancel and start over.

Good luck.

---

### Post by aysiu on 2006-10-19
> **kernco said:**
> Here's another question.  I should probably just start a new thread:  For data I want to work with from both OSs (read and write), should I put it in the Windows NTFS partition, or should I use a Linux FS (I haven't looked, but I assume there are windows programs out there that allow use of ext or other filesystems?)
Read this:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by gn2 on 2006-10-19
This might be useful: [http://www.fs-driver.org/](http://www.fs-driver.org/)

Each OS can read from the other, it's just writing that's the problem.

---

### Post by kernco on 2006-10-20
Thanks guys.  I can now dual-boot Windows XP and Ubuntu.  On my 80 GB hard drive, I have ~15GB for my Windows parition, ~10GB mounted at / in Ubuntu, ~1.5GB swap, and the rest an ext3 partition mounted at /home in Ubuntu, and read/writable from Windows XP using the fsdriver program (link posted above).

---

