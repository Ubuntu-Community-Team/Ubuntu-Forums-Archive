---
title: "Feisty Fawn boot very slow (15 min).  Edgy fast."
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by am7146 on 2007-07-22
I have an Averatec ee3270 laptop that had windows on it and I just downloaded, burned, and installed 7.02 on it from scratch--blew away Windows, whole disk.  Booting is impossibly slow. Here's the sequence.
[LIST]
[*]GRUB -- Fine.
[*]Booting with the splash with the progress bar, fine.
[*]X loads and the mouse pointer becomes very unresponsive.  It is frozen for one second, then jumps to where you moved the mouse, then freezes again.  Then when it turns to the spinning circle it keeps hanging and jumping.  The circle only clicks one dash forward every few seconds.  
[*]Login Screen paints in big blocks from the top--it paints about 1/4 of the screen, then 1/4 of the screen, and so forth until it finishes. 
[*]I can log in (slowly) and then the desktop comes up very, very slowly.  
[*]After about 10 minutes of really slow activity, suddenly the machine is fine.  Performance is just fine.  Mouse comes back, and the machine is great.  
[*]If I reboot, it does the same thing.
[/LIST]
I edited grub and put in noapci and that let the mouse move freely--it was no longer jittery and the spinner spun smoothly, but the machine was just as unsuably slow as before.

I blew away 7.x and installed Edgy and it works great.  Super fast boot.  No problems in running.

Unfortunately, I didn't know about bootchart before I blew it away or I would have run it.

Thoughts??  Should I just stay on Edgy?  I've got it working pretty well now. 

Can I "image" my current install so I can get back to it easily if I try installing Feisty Fawn again?

Andy-

---

