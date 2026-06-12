---
title: "Fesity Install Disk Error"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by flackboy on 2007-04-24
Greetings everyone,
   After serious problems upgrading from Edgy to Feisty (got to installing wvdial and froze solid), I decided a fresh install would be the best move.  

I downloaded the latest build direct from Ubuntu verified it, cut it to CD, verified it again and tried to install.

As soon as it gets past the initial Ubuntu splashscreen, it pauses and the floppy disk light - not the CD light comes on.

Then after a long pause we get "Buffer I/O error on device sr0 [or fd0] logical block [0..5]

I'm trying to install on a Samsung P20c laptop which has had no problems whatsoever with Edgy.  It has a drivebay system which currently has the CD/DVD-Rom inserted.

Any thoughts or pointers, people?

Thanks,

Brian...

---

### Post by ABCC on 2007-04-24
If I'm not mistaken you can choose to verify the integrity of the install disk from the Ubuntu splashscreen menu you speak of. There's probably an error in the disk you've burned, that check will show if it's a coaster or not. 

If/when you burn a new one, use a program like k3b which allows you to verify the disc right after burning. My box makes toast out of about 4% of what it burns, ymmv.

HTH,

ABCC

---

### Post by flackboy on 2007-04-25
Hi ABCC,
   Thanks for replying.  The disk itself is fine.  I did verify the checksum - and the disk - and it boots no problem on two other PCs in the house.  

The problem *seems* to be that this new Feisty install misidentifies my CD as a floppy drive (they fit in the same drive bay).  If I use a 6.10 Dapper disk, it works no problem, but this new build is giving me no joy.  I've tried three different disks now (just to be on the safe side) and they all give the same problem.

B.

---

### Post by ABCC on 2007-04-25
Have you tried passing different boot parameters to the kernel? Also, have you verified that  the current setup works with an edgy cd recently?

---

