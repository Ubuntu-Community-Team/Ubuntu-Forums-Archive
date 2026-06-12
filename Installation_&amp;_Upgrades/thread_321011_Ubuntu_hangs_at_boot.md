---
title: "Ubuntu hangs at boot"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by tommyhat on 2006-12-18
Hi there, I've had some problems with ubuntu for a while now, trying to get it to install. The whole process is kind of flaky but now it's finally installed. I gleefully booted my new OS and to my horror find it hangs at "Mounting image of OS" or something like that (second operation in booting).

I tried running the ubuntu recovery and that always hangs in the myriad of output before it even starts up.

I can only assume the problem lies in the fact I had to cancel installation before and it threatened to "leave my computer in an unusable state". But there was nothing else I could do besides creating a new partition and losing everything. Is there some kind of cleaner or fix? Any advice?

---

### Post by bulldog on 2006-12-18
Do a reinstall on the same partitions,format them and install again,it's only 30 minutes.
To repair this install cost much more time :D

---

### Post by tommyhat on 2006-12-18
Thanks!

If this doesn't work, however, how does one repair an install?

---

### Post by bulldog on 2006-12-18
Repair isn't something you can easily do,you have to gather a lot of information from the user which install is broken.
It's much faster to reinstall ubuntu,specially if you haven't install much software.

Reinstalling should work if you have a valid ubuntu cd,did you check your cd before you installed it?
Go through the install till you get to the partitioner,choose manual partitioning and mount your / as / and your swap as swap.
Check them to be formatted,swap as swap and / as ext3 and proceed with the install.
Don't interrupt the installation or you have a broken ubuntu again.

---

### Post by theurgy on 2006-12-18
[http://www.ubuntuforums.org/showthread.php?t=299929&highlight=Inspiron+1501](http://www.ubuntuforums.org/showthread.php?t=299929&highlight=Inspiron+1501)

---

