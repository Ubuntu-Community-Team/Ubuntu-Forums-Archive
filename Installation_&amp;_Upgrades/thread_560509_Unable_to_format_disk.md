---
title: "Unable to format disk"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by mikemn84 on 2007-09-26
Okay, so Ive got a Sony Vaio laptop that had Windows and Ubuntu installed through wubi on it.  Due to unknown reasons (it wasn't in my possession at the time), it is now unable to boot to any OS.  I am willing to simply erase everything and start over, but the problem is, I can't reformat.  The hardrive had some "bad cylinders" or something that prevented gparted from wiping it.  So I tried the chkdsk, fixboot and fixmbr utilities through a windows install disk.  None of these have done any good, in fact chkdsk wont even run - it just says "one or more unrecoverable problems have been found."  So then I tried zeroing the disk from the live CD, but it freezes the system somehow before finishing.  Ive tried a number of other solutions from the ubuntu help docs [_here_]("https://help.ubuntu.com/community/DataRecovery"), but nothing has worked.

So after I butchered the hardrive with my attempts to save it, I can't even wipe all my data and start fresh (this time it would be without wubi and windows incidentally).  Isn't there some way to just erase the entire disk regardless of the issues on it right now?  Any help would be a lifesaver as this is a company computer.

Thanks.

---

### Post by wpshooter on 2007-09-26
Yes, hopefully you have another computer.

Try.

[www.killdisk.com](www.killdisk.com)

---

### Post by Mizipzor on 2007-11-13
I have more or less the same problem. Neither Partition Magic 8.0, the Windows Vista install cd or qtparted can format the disk. Im gonna download and try killdisk, to kill it and then, hopefullyl, reformat it.

Does the ubuntu livecd have any formatting programs I can try? As a last attempt.

---

### Post by zvacet on 2007-11-13
Yes.It is part of installing process.

---

### Post by az on 2007-11-13
It sounds like the hard disk is unusable.  If the hardware is borked, there is no software that will fix it.  

You need to buy another hard disk.

---

