---
title: "Uninstall Dual Boot Question XP/Ubuntu"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by Bus_Driver on 2007-01-21
I tried installing ubuntu - and I got that /bin/sh can-t access tty; job control turned off error that it seems is pretty common.  

I wanted to remove the dual booting partition - but I have a question.

If I boot into XP repair for the MBR - and fixmbr as it says to do - willit get rid of all my partitions?? Not just the one that ubuntu created?

If so - that's pretty stinky - I guess I should have looked into this a bit further first.

Second question  - any thoughts on how to fix that /bin/sh can-t access tty; job control turned off error?  I replied to someone else who was also having the problem - I can't seem to find how to fix it.

Thanks for any help you can provide.

:confused:

---

### Post by fritz_monroe on 2007-01-21
It should not get rid of any partitions.  fixmbr is **supposed** to just fix the MBR.  It basically just puts the system back to booting into Windows.

---

### Post by Bus_Driver on 2007-01-22
OK - but it actually says - when I typed fixMRB that it could make partitions unaccesible.

---

### Post by fritz_monroe on 2007-01-27
Did you get this straightened out?

That warning would be their way of protecting themselves.  Because the warning is there, if you accidentally destroy your partitions somehow, they can't be blamed for it.

One thing I didn't notice before.  Fixing the MBR shouldn't even get rid of the Ubuntu partition, it should only fix the Master Boot Record and cause the system to go right into XP.  You may get some additional info by posting to a straight Linux forum instead of a Ubuntu specific one, or even to an XP forum.  Good luck.

---

