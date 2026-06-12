---
title: "What happened to my data on second hd during install?"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by ironhulk on 2006-06-13
I upgraded from breezy to dapper via apt.  I had some trouble with a wireless card ([http://www.ubuntuforums.org/showthread.php?t=132980]("http://www.ubuntuforums.org/showthread.php?t=132980")). It's a long story, but I decided to go back from scratch.  Not, however, before backing up most of the important stuff to a second hard drive.

I got everything up and running, mounted the second hard drive and found nothing but a lost and found directory.  It was/is formatted as ext3.

This isn't a huge issue because its more of a development box.  I upgraded a laptop successfully to dapper, but I have another machine, similar to the dev one, with a raid array containing some actually important stuff and I don't want to risk the same happining.

I was wondering if anyone had heard of anything like this?  Or any other suggestions before I upgrade my other machine?

Thanks a lot!

---

### Post by Sutekh on 2006-06-14
Which install method did you use?    The LiveCD (sorry Desktop CD) then install from that?   Or did you use the text Install CD (Alternate CD) to install Ubuntu (like you would have Breezy)?

 I haven't used the LiveCD method, because I was a little skeptical.

If you used the text install, you need to make sure that the partitions have a **K** next to them.    **K** for keep, not **F** for format.  Then double check in the confirmation screen that they are not due to be formatted.  Otherwise they shouldn't be touched.

If you are sure that this is not the case, I'm not sure where to look.

---

