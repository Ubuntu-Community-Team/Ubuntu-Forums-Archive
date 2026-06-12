---
title: "Install in Windows fails on XP and Vista"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by rmmsr on 2008-06-03
I built a CD from a download of the 8.04 version of Ubuntu Linux.  I have a Vista system and an XP system.  I was able to run the no system modifications Linux on both machines.  I was especially pleased that wireless worked on both (wildly disparate) machines.   I used PartitionMagic on my XP machine to create Linux swap and EXT3 partitions.  I was then successful in installing 8.04 on that machine.  The GRUB dual boot worked well.  I failed on both machines in trying to create the “Install in Windows” version of 8.04.  In each machine I reached the point “creating image  N of 733 MB”.  Writing would continue until 100% of the image was written.  I then received the message, “Could not access CD, please make sure other applications are not using it and try again.”  Obviously no other application was using the CD.  Trying again merely repeated the image write and error message.   Is there a fix for this problem?

---

### Post by dstew on 2008-06-03
This sounds like [this bug]("https://bugs.launchpad.net/wubi/+bug/207137"). Some users found that burning a DVD-RW instead of a CD solved it. Others put the .iso into the same directory which is executing wubi.exe.

---

### Post by rmmsr on 2008-06-03
Thanks for your helpful reply.  I tried creating a DVD but that fared no better than creating a CD.  The link you provided provides  some other possibilities which I will explore.  Thanks again.

---

