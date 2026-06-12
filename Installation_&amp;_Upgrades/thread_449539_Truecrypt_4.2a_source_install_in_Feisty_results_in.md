---
title: "Truecrypt 4.2a source install in Feisty results in HUGE /usr/src/linux directory"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by vedace on 2007-05-20
I compiled Truecrypt 4.2a from a patched set of source files to install it on my Feisty machine running kernel 2.6.20-15.  The .deb for 4.3a didn't work, and I killed make after it spent 40 minutes  inhaling CPU cycles trying to compile 4.3 from source without getting anywhere, so I went with 4.2a. 

Truecrypt 4.2a is working just fine.  The problem is, I noticed that all of a sudden, my /usr/src/linux-source-2.6.20 directory is about 1.8 GiB in size, even though a freshly untarred version of that folder (off the repos) is only 250 MiB (and the tarred version is a pithy 40 MiB).  What could Truecrypt possibly have done to make it so huge?  I know that it had to compile kernel modules, but kernel modules don't go in the source directory, do they?  I figured there was a separate (more reasonable) place for compiled kernel modules.  When I compared the freshly untarred directory to the modified directory in my /usr/src, it was plain to see that there were many many additional files all over the place, and I have no idea how to explain their presence but that they were put there by Truecrypt during installation.  I considered removing and reinstalling Truecrypt from source, but when I remember how long the process took the first time, I'm hesitant to consider repeating it in case something goes awry.  Any ideas?

Thanks.

---

### Post by TheWizzard on 2007-05-20
did you follow this installation guide: 
[http://www.ubuntuforums.org/showthread.php?t=199367](http://www.ubuntuforums.org/showthread.php?t=199367)

why did you kill the make proces? it takes a few hours ...

---

