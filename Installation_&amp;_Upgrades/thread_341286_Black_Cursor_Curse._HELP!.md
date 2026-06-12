---
title: "Black Cursor Curse. HELP!"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by kubstix on 2007-01-18
So it seems I am having the same exact problem as everyone else.  I have tried 5 different types of media, burned at 4x, everything.  No matter what option I chose (Even check cd for defects) it just goes to a black screen with a cursor in the upper left hand corner.  It just sits there and does nothing.  I tried the alternate disc as well, any option I chose does the same thing.  I heard people talking about Nvidia, ect.  This is an onboard Intel Display so that is out of the question.  Tried LCD and CRT, nothing.  Can someone please assist me?  And dont post the 3 common questions either.  I tried 4x, used MD5SUM, ect.  Thank You.

---

### Post by taurus on 2007-01-18
The fourth question is Dapper Drake, 6.06!

---

### Post by kubstix on 2007-01-18
Unfortunately I cannot do this.  I work for a high school and the programming kids and instructor want Ubuntu.  However, I did notice the DVD drive is a SATA drive, which is extremely odd.  I have a similiar HP computer sitting next to me with an IDE DVD Drive and it has no problem with installing.  Is there something that needs to be done in order for linux to recognize its installing from a SATA interface rather than IDE?  Also, since HP makes there own motherboards for custom, there is no IDE Controllers on the MB, just SATA.  So that kind of sucks as well.  Thanks for the help.

---

### Post by taurus on 2007-01-18
Dapper Drake IS Ubuntu.  

[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

---

### Post by kubstix on 2007-01-18
I would prefer installing 6.10 because that is what the students voted on and staff.  I feel the issue is related to the dvd drive being SATA.  I have an almost identical setup next to me with the exception of an IDE DVD drive and it loads without a problem.Assuming linux setup loads some sort of general ATAPI drivers for the drives is there anything I can do to have it recognize the SATA DVD Drive?  Thank You.

---

### Post by taurus on 2007-01-18
Just so you know, Dapper Drake is a LTS (Long Term Support) so it would probably work on more hardware than Edgy.  Again, it doesn't hurt to download Dapper and test on one machine to see if it runs at all!  And if the kids really want to use Edgy, upgrade Dapper to Edgy and they wouldn't even know the difference.  ;)

---

### Post by kubstix on 2007-01-18
Just tried Dapper Drake.  Almost the same issue.  No matter what I select it still freezes but at least gets as far as Uncompressing Linux....OK, booting the kernel.  Then it just sits there and does nothing.  I dont know what else I can do, but I got to get linux on these computers somehow.  Thanks for the help.

---

### Post by taurus on 2007-01-18
What the spec of those machines anyway?

---

### Post by kubstix on 2007-01-18
DC5700 Custom
Pentium D 3.2GHZ
2GB RAM
Onboard Intel Video
Onboard Realtek High Def
Onboard Broadcom Nextreme GB Ethernet
80GB WD SATA 3.0
DVD-ROM/CDRW SATA Drive

Thats about it.  I dont understand why its doing this.  I ruled out a bad DVD drive as well.

---

### Post by taurus on 2007-01-18
I am not sure either but since Ubuntu can't install on those fast machines, maybe it's time to look at another friendly Linux distro.  You can check out Fedora Core 6!

[http://fedora.redhat.com/](http://fedora.redhat.com/)

You can download the 5 CDs or the 1 DVD version and since you have a fast network connection at school, go for the 1 DVD version.

---

### Post by kubstix on 2007-01-18
It shouldnt make a difference that XP is already installed on the hard drive should it?  I have corporate edition installed on a 25gb partition, another 25gb partition, a 20gb partition, and a 7GB partition for Ubuntu.  However all 3 additional partitions are just RAW, not formatted or a file system on them.  In case that helps.  I just read the 965 chipset just doesnt have PATA controllers period.  It seems numerous people are having trouble with installing linux on this particular chipset.  Has anyone figured this out?  Thanks.

---

### Post by MrThursty on 2007-03-19
I found this on the HP website. Hope it helps.

[https://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=1090380]("https://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=1090380")

---

