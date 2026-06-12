---
title: "Kernel 2.6.19-1"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by Sha-baz on 2007-01-05
Imagine that I have a CDROM that fails to be recognized due to a [bug in my kernel (2.6.17-10-generic)](http://www.archivum.info/linux.debian.bugs.dist/2006-12/msg05145.html). According to the Kernel Archives, kernel 2.6.19-1 is the most recent stable kernel available.
 
What exactly would it take to upgrade my kernel to version 2.6.19-1? Just a few pointers are enough to get me in the right direction, but I can't seem to find a lot about this issue, that's why I think I am missing something... am I?

---

### Post by Sha-baz on 2007-01-08
Problem solved. If anyone who reads this has the same problem, find your sources.list file and replace the word 'edgy' for 'feisty' to make Kernel 2.6.20 available in your package manager. 
 
This problem occured on my VAIO FS215B laptop, which had a Pioneer DVR-K15 dual layer CD/DVD writer. This writer is not recognized by Kernel 2.6.17 and older.

---

### Post by martinko01 on 2007-01-08
I tried to upgrade to 2.6.19.1 by compiling the kernel sources from kernel.org but it did not work for me.

So your solutions sounds very interesting to me: I understand you just replaced edgy by feisty in sources.list -- but feisty is unstable ... can you describe a little more in detail how you manage to JUST upgrade the kernel without getting feisty instability ?

thanks

---

