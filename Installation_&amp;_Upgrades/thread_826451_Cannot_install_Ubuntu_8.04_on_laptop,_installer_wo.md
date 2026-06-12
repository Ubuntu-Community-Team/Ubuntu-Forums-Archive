---
title: "Cannot install Ubuntu 8.04 on laptop, installer wont create ext3 file system"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by akowalski on 2008-06-11
Hey, 
I am really new to Ubuntu and Linux, and Im just trying to get it up and running on my Dell Inspiron 8200.  I had it working a few days ago, but after i tried to download and install some updates it sort of went to pieces.  Each time i try and reinstall Ubuntu, no matter if i let it use the entire disk or if i do it manually, it never installs past 5% in partitions formatting.  It stops right when it says "creating ext3 file system" or something close to that.  
I have tried clearing all partitions in the live cd and also erasing the hard drive completely with this boot cd I have.  I have even gone back and made a new Ubuntu install cd thinking maybe my CD was the problem.  The same problem keeps coming up when I install.   Could it be that my hard drive is just failing? everything seems to suggest that its working fine but I cant think of anything else...

---

### Post by Pumalite on 2008-06-11
Check your drive with rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
(I think it has a partitioner too)

---

### Post by swguy on 2008-06-11
Did you do an integrity check on the CD?  I've had a few go bad after a single install.  Now I only use CD-RW data discs so I can rewrite them if there's an issue.

---

### Post by akowalski on 2008-06-11
Yea, I did an integrity check with both cd's I used. they both seem fine, so I think the problem is in my computer.  It is kind of old, which is why I think it could be the hard drive starting to fail. Ill try that link up above and see what happens.

---

### Post by Pumalite on 2008-06-11
Try to use only CD-R of good quality.

---

### Post by akowalski on 2008-06-12
Iv been burning my cd's on maxell CD-R pro cd's. Are those good quality?

---

### Post by akowalski on 2008-06-12
ok, so i used that system rescue boot cd that was posted above, and i partitioned the hard drive on there. I then went into the installer cd and clicked manual. I told it to use the partitions already amde and to not format them. Then it skipped the part where it always freezes up and now it seems to be working fine. thanks for the help!

---

### Post by Pumalite on 2008-06-12
You are welcome. Good luck.

---

