---
title: "Mounting Partitions in Gparted"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by Dazarus on 2006-12-29
I just made two partition from a current drive that was being used by windows, using the free pass I made one partition of 15gig for the root and one partition of 90 gig for files. I go to install the program onto the 15gig part. and it says no file system... I check the info on the drive using Gpart and it says unmounted... do I need to mount this before use and if so how can I, I'm running of of the liveCD and my current op system XP... PLS help:confused:

---

### Post by Bartender on 2006-12-29
> **Dazarus said:**
> I just made two partition from a current drive that was being used by windows, using the free pass I made one partition of 15gig for the root and one partition of 90 gig for files. I go to install the program onto the 15gig part. and it says no file system... I check the info on the drive using Gpart and it says unmounted... do I need to mount this before use and if so how can I, I'm running of of the liveCD and my current op system XP... PLS help:confused:
 
What did you use to do the original partitioning?  When you say you used Gpart do you mean you started up a LiveCD and went into Gnome Partitioning Tool?  You can't partition or modify a mounted partition.  I think you're a little bit confused about mounting.  
What do you want to accomplish?  Are you trying to dualboot or wipe this drive entirely?

Either way, I'd download [GPartedLiveCD]("http://gparted.sourceforge.net/livecd.php") (GPLCD), make a bootable CD from the download, then boot from the CD.  Wipe out those partitions you tried to make.  Then rebuild them using the GPLCD.  Make both ext3.  The data partition could be extended, but I'd make the / partition primary.  Take a look at my how-to in [post #9]("http://www.techsupportforum.com/alternative-computing/linux-support/131773-dual-linux-os.html")  for some ideas on how to maneuver around with GPLCD.  It was written for an all-Linux HDD but still should help you.  Then when you toss in your install CD (alternate or Live version) it should recognize the partitions.  When you install Ubuntu it might still want to format the partitions.  If in doubt whether you did it right just let it even though it's probly not necessary.

Hope that helps

---

### Post by Dazarus on 2006-12-29
when I first partitioned them it was using qtparted on a knoppix live cd, because the Gparted livecd I DLed from that same site keeped freezing after getting a "failure" error while trying to launch the kernal or whatever used to start


just go the error again

" Fatal server error
       caught signal 8. server aborting "

---

### Post by Dazarus on 2006-12-29
ok, so I finally got the partitions set I think... I took drive that runing windows and took it off the list during the installation I set my 15 gig drive as the /  and the 103 gig drive as the swap file one. When It loaded finally my 15 gig part. says floppy one and the "file system " is the 109gig but it wont tell me the size.... sorry for pounding the forums I am reading all the how too stuff

---

