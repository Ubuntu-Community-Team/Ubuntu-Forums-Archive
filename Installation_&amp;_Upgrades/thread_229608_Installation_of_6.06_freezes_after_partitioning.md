---
title: "Installation of 6.06 freezes after partitioning"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by mythryn on 2006-08-04
I searched the forum, but couldn't find anything that directly pertained to this problem.  Please let me know if I'm wrong.

Problem:  During installation, after completing partitioning, I click the "next" button and the computer freezes.  Mouse won't even move eventually.  Previous version of Ubuntu (5.10?) installs without a problem.

System:
Shuttle XPC SK21G
AMD Sempron 2800+
1 gig RAM
SATA Seagate 80 gig HDD
ATI all-in-wonder 9600XT

---

### Post by irw on 2006-08-04
How old is your CD iso?  I had this with an early iso downloaded soon after Dapper came out, but a couple of weeks later aa newly downloaded iso created a disk from which it worked fine.

I am assuming there was a bug that was fixed ... it may have been a dogy CD or luck ...

---

### Post by avtolle on 2006-08-04
[http://www.ubuntuforums.org/showthread.php?t=228616&highlight=Shuttle](http://www.ubuntuforums.org/showthread.php?t=228616&highlight=Shuttle) leads me to believe that your Shuttle may be "cursed" to some small extent. Note that use of the prior kernel avoids the action complained of in the thread; i recall reading a very long thread in early June that was started by someone with a Shuttle complaining of the behavior similar to what you are experiencing, If you haven't already done so, you might search w/Shuttle and see what appears. HTH.

---

### Post by mythryn on 2006-08-18
I eventually got it to work.  I don't know what the issue was, but when I used the partitioning tool on the Ubuntu livecd to delete all my partitions and create new ones, it worked.  The partitions I had had been made a while back with Knoppix and seemed to work fine with Debian.  ???

---

