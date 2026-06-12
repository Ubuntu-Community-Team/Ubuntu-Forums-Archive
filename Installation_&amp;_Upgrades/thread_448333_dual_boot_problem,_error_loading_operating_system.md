---
title: "dual boot problem, error loading operating system"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by vecryn on 2007-05-19
Sorry for posting this in two separate areas of the forums, wasn't sure which section this would be best located so i'm asking in two sections.

Ok, first question I guess is can you have Windows xp64bit and ubuntu having a dual boot system?  I'm just wondering if xp64 is what is causing this issue.

I have it setup so far like this.
C drive is 62gig Master drive
D drive is 100+gig about 170gig or so (I partitioned a 250gig drive having one partition 62gig, the rest went to the other partition.)
E drive is a slave HD 40gig

I installed windows xp64bit onto the 62gig partition, booted just fine, installed all the updates etc, then installed ubuntu 7.04 onto the 40gig slave HD.  When the install was complete it asked me to reboot, and to remove the install cd from the cd tray.  I did this and as soon as it loaded up it got to the point where it would boot saying Boot from cd, then since no disks are in the cd try it tried booting from the hard drive and gave me "error loading operating system"

If I put in the windows xp64 install disk it will get to this part again, and says to boot from cd press any key.  if I touch nothing at all it will jump over to booting up ubuntu.  Windows xp64 is in this list of options of what to boot but if I select it nothing happens.  it will load ubuntu though, but only if the install disk is in the tray, either windows or ubuntu's if not it gives the error loading operating system message.  So i'm not fully sure what the problem is here.  it seems like a boot issue, but at the same time it wont load windows xp64 at all even with the cd there.  I tried repairing it and I still have the same problem.

---

### Post by southernman on 2007-05-19
> C drive is 62gig Master drive
D drive is 100+gig about 170gig or so (I partitioned a 250gig drive having one partition 62gig, the rest went to the other partition.)
Is it possible that you were in a hurry when selecting the partition to install ubuntu? That is the only reason I can think of, why you can't even boot into your winders system.

---

### Post by vecryn on 2007-05-19
nope I clearly selected the slave drive 40gig.  I just think there is a problem with it trying to figure out which one to load, but i'm still not sure why it wont load windows period.

---

### Post by southernman on 2007-05-19
My other *guess* would be a grub / mbr foul up.

Searching the forum with your thread title gives  [this list of results]("http://ubuntuforums.org/search.php?searchid=20450257"). The 11th and 12th thread look to be good candidates for a solution.

---

