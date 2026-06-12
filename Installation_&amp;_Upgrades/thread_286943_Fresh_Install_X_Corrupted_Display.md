---
title: "Fresh Install X Corrupted Display"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by mdowney on 2006-10-28
Ok, so I have been using Dapper happily and decided to do an upgrade to 6.10 final.  Everything appeared fine, however I had a ton of hardlocks in Gnome.  So I decided to do a fresh install of Edgy, first the liveCD couldn't get to the Gnome desktop, i would get corrupted graphics on the monitor connected to DVI, and just a cannot display message on the other monitor connected to Analog.  I  tried both the regular and safe graphics mode, both had the same results.  I figured I would try the alternate install CD, hoping that it was just a bug in the live CD.  Unfortunately I got the same results after installing.  If I try to use another terminal the graphics are corrupted as well, cannot read a thing just a huge gray mess.  Here is the pertinent info for my computer in case someone can help me:


Athlon XP 2800+
1GB DDR Ram
Ubuntu installed on /dev/hda1
GeForce 6600 AGP 8X 256 MB with one LCD connected to Analog and Another connected to DVI.

Is there a way I can stop X from starting up when I boot so that I can try to install the correct video drivers?  Like I said all virtual terminals are corrupted as soon as X starts.  The splash image appears perfectly, and I had no problems in Dapper so I'm sure its just a driver problem.  Let me know if I can provide more info to get this solved...guess I will be using Windows for the day.

---

### Post by Schluppy on 2006-10-28
> Is there a way I can stop X from starting up when I boot

Yes. Hit the 'escape' key after your computer POSTs then select your 'recovery mode' kernel from the list.

---

### Post by mdowney on 2006-10-28
Thanks Schluppy, all is well now :)

---

