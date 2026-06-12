---
title: "Can't Install - Mounting Root Filesystem hangs"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Gamezguy on 2006-11-06
Hi,
I've tried to install my i386 Ubuntu 6.06 disc on my AMD64 3200+ computer, but when it gets to "Mounting Root Filesystem..." the computer hangs. IT also happens with my Edubuntu, Kubuntu, and Xubuntu CDs, and the 6.10 Kubuntu I downloaded the other day. The Debian i386 works perfectly, so I don't think it's the architecture. Am I missing something? My AMD64 CD works fine. I've got a Debian installation already on it, so it may be trying to use its swap file. :-k 
Thanks.

---

### Post by Najand on 2006-11-06
Hmm, try using the LIVE CD. Then open a terminal and use the command:
```

fdisk -l

```
and find your root partition (for example: */dev/hda1*) and then check your file system using
```

fsck */dev/hda1*

```
and see what is the problem with your disk!

---

### Post by Gamezguy on 2006-11-06
This is what happens when I try and RUN the live CD! Should I remove my previous Linux install, would that help?

---

### Post by Najand on 2006-11-06
Same result when running in recovery mode?

---

### Post by kevinsun on 2007-02-09
I'm having the same trouble. During the time that I upgrade my system.  Maybe the battery ran out. So, when I got back to my desk, it already stopped running.  Now, I can only get to the point of mounting the root system.  It hangs.  I can't even boot to the recovery mode which previously is very stable.

Now, how can I restart an unsuccessful/interrupted upgrade?  I just want to use back my old dapper.

Please help.

---

