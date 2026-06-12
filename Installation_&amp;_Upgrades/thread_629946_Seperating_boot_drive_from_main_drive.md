---
title: "Seperating boot drive from main drive"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by ac7ss on 2007-12-02
I have an interesting system that has evolved into:
AMD 64 MB
30gig IDE
250gig SATA

Single boot system running ubuntu.

Right now the SATA is being mounted under /home

I am running out of space on the IDE and want to symlink some of the directories to the SATA. Which ones are safe to do so with, which ones are smartest to do it with. I figure /usr would work ok. but want to be sure. I know that /dev and /proc would be a bad idea, as well as /log.

Any suggestions are appreciated.

---

### Post by froy02 on 2007-12-02
Just automatically mount the 2nd drive and you have a 250 gb data storage.  Move all your home data to that drive and 30 gb is actually very large for just the ubuntu operating system.
I used a 30 gb HD for ubuntu operating system and my data is all in a 300 gb 2nd drive. I do not put any data, music, documents, downloads, spread sheets on the 30gb HD. The 30 gb is only for the installation of the programs that i use.  Right now with all the programs i installed it only uses 4 gb so I still have 26 gb to install more programs.

---

### Post by ac7ss on 2007-12-03
well, cleaning up the apt cache freed up about 5 gigs. (just updated to gutsy.)

Still the question remains. (I do mount the 250G as home. it's the libs that take up the room.)

---

### Post by ac7ss on 2007-12-15
Problem solving itself. The / drive was a 10 gig, not 30. but is now dying. I am replacing it with a 80 gig and that should fix it. (besides that, now I will be making a clean install of Gutsy.)

---

