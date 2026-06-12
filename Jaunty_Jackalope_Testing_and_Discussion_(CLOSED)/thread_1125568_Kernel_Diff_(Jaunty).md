---
title: "Kernel Diff (Jaunty)"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by windexh8er on 2009-04-14
So this isn't really a dist specific question, but it has to do with Jaunty and I figured this would be a decent spot to post.  My question is that I have just gone through the process of rebuilding the 2.6.28 kernel via instructions found here:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Problem is that after I was all done (my kernel compiled and installed fine BTW) I realized that what I compiled was not the latest.  It was the base 2.6.28 and there are two files that are probably required to get the base linux-2.6.28 directory up to snuff.  These are as follows:

-rw-r--r--  1 root src  6.9M 2009-04-08 00:04 linux_2.6.28-11.41.diff.gz
-rw-r--r--  1 root src  2.0K 2009-04-08 00:04 linux_2.6.28-11.41.dsc

Anybody know, off hand, how I can merge that diff in to the:

drwxr-xr-x 25 root root 4.0K 2009-04-14 14:29 linux-2.6.28

...directory?  Wasn't referenced in any docs I ran across.  Any help would be much appreciated!!!

Kind regards and TIA!
--windexh8er

---

### Post by kurros on 2009-04-14
I don't know which steps you used but if you used the apt-get source command then the ubuntu patches were applied.

```
dpkg-source: extracting linux in linux-2.6.28
dpkg-source: info: unpacking linux_2.6.28.orig.tar.gz
*dpkg-source: info: applying linux_2.6.28-11.41.diff.gz*
```

Otherwise you can run dpkg-source -x linux_2.6.28-11.41.dsc

---

### Post by windexh8er on 2009-04-15
Sweet, thanks!  I knew I was missing something with that dsc.

OK, new question...  I totally hosed up that test platform in making some other changes so I started from scratch again.  In doing so I decided to try pulling the kernel source via git as recommended on the kernel site:

[https://help.ubuntu.com/community/Kernel/Compile#Build%20the%20kernel%20(when%20source%20is%20from%20git%20repository,%20or%20from%20apt-get%20source](https://help.ubuntu.com/community/Kernel/Compile#Build%20the%20kernel%20(when%20source%20is%20from%20git%20repository,%20or%20from%20apt-get%20source))

Now my question is everything is working but I need to recompile l-r-m.  Phack -- seems like you can't pull that via git?  So now I'm wondering if it's going to be harder to maintain the one to one relationship?  Both say they're using Ubuntu-2.6.28-11.41 (phew!), but I just want to make sure I'm not making a bad move by needing to have l-r-m and doing half via apt and half via git.

Thoughts and/or recommendations? TIA!!!

--windex8er

---

