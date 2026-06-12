---
title: "Help dual booting"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by LopsidedElf on 2006-06-18
I recently decided to start from a clean slate and repartition everything and reinstall windows and ubuntu from scratch.

I partitioned my drive to have:
/hda1 ntfs 20gig
/hda2 ext3 5 gig (for /)
/hda3 ext3 206 gig(for /home)
/hda4 swap 1.88gig (unneccsarily large i know)
All Primary partitions

my question is in which order should I install my OS's should i install windows first then Ubuntu, Thanks

---

### Post by aysiu on 2006-06-18
Windows first.
Then Ubuntu.

Swap does seem big, but with that large a hard drive, you're probably not hurting for space.

---

### Post by LopsidedElf on 2006-06-19
Thanks for your help.
Is it ok that all my partitions are primary? i was a little confused about that part. 
Also I can get windows to recognize my /home in ext3 right? How would i do that?
Thanks again

---

### Post by aysiu on 2006-06-19
Well, four's the limit, so you should be okay.
To get Windows to recognize Ext3, you'll need to install [http://www.fs-driver.org](http://www.fs-driver.org)

---

