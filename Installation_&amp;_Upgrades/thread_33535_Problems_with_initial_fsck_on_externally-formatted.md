---
title: "Problems with initial fsck on externally-formatted partitions"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by pointym5 on 2005-05-11
I have a few data partitions formatted (ext3) under Fedora Core 3.  The Ubuntu installer partition tool sees those partitions just fine, and it allows me to give mount points for them.

Once install completes, however, and the system comes back up, those filesystems seem to confuse e2fsck and it fails.  (Why?  I don't know; e2fsck says, "get a newer e2fsck".)

What's worse is that once the fsck fails, the boot sequence gives me a prompt wherefrom I could conceivably fix the problem (by getting rid of those filesystems in fstab I guess).  However, at the point the shell is started the system hasn't yet gotten the UHCI USB stuff ready - so my USB keyboard doesn't work at all!! Only option: hard reset and repeat install procedure without mounting those partitions.

 ](*,)  ](*,)  ](*,) 

That seems like a pretty severe boner to me.  I can understand the issue with the fsck version, but leaving the system completely stranded seems pretty unfriendly.

---

### Post by cshen on 2005-05-19
I had the exact same problem.  What is unusual is that when I mounted the ext3 filesystem, it mounted without errors and behaved normally.  I also looked for an update to the e2fsck program using apt, but none was available.

 Any ideas on what causes this would be greatly appreciated.

---

### Post by vince-ubuntu on 2005-05-28
I have the same problem. I have been told to run e2fsck on the partition causing problem, but the program says that checking a mounted partition can cause SEVERE damage. I usually backup when I see messages like that. 
Maybe the solution is to boot on the live ubuntu CD and THEN run the program. I haven't tried yet, and won't be able to do it today since I don't have the CD with me right now.
Tell me if you figure out a way to do that.
V

---

### Post by vince-ubuntu on 2005-06-12
Hi,
here is the solution to this problem:

[http://www.mail-archive.com/trilug@trilug.org/msg26479.html](http://www.mail-archive.com/trilug@trilug.org/msg26479.html)

enjoy your ubuntu!
Vince

---

