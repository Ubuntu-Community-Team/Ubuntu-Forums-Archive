---
title: "Moving from one machine to a new one"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by Neon John on 2011-03-29
I just bought a brand new Dell Optiplex to replace my several year old creaky old laptop.  I'm running 10.04 Lucid.  Since the new machine and my laptop both had 350 gig drives, I used Clonezilla to clone the laptop drive to the new machine's drive.

This boots and runs OK but the machine doesn't seem as fast as it should be considering the age differences.  And there is an amount of accumulated detritus from the many upgrades over the years.

So I have three questions.

1.  Does Linux do hardware detection at installation or boot time?  In other words am I OK with the cloned drive or should I do a clean installation that would detect, for example, the dual cores and use them optimally.

2.  If I should do a new install, how do I get all my current environment over to the new machine?  I know to copy /home/jgd and I found instructions for copying my installed packages but I have a lot of customizations that those two probably would not get.  Things like backup-manager automatically backing up my home partition and unison keeping a couple of external drives synchronized as a poor man's RAID.

3.  If the answer to #2 is that there is no easy way and if hardware detection is done at install time then is there a command or commands that I could run to cause Linux to re-discover the hardware on this machine?

I'm sure that this has come up before but I spent last night searching the archives and found nothing.

Thanks in advance,
John

---

### Post by mörgæs on 2011-03-30
All things considered I would go for a fresh install. 

If you want to try it before wiping the present system, you could free some space and create a new partition for a test install. If it works well then just move your user files and **carefully selected** configuration files / scripts here.

---

### Post by Mark Phelps on 2011-03-30
While I would also recommend a clean-install for the new PC, I also did a migration to a new PC recently, without a clean-install, and Ubuntu 10.10 found and installed all the necessary drivers without any problems.

---

