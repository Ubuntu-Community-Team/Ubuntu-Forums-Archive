---
title: "Ubuntu 7.10 Hangs"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by agentno4 on 2008-02-07
So I decided it was finally time to dual boot my desktop box with Windows XP and Ubuntu. ( I have had a similar setup on my laptop for two years.)  After downloading the latest version of Ubuntu, I ran into tons of problems with the live cd/install hanging.  I figured no big deal, downloaded the alternate cd, and installed away.  Hooray...success I thought....Nope.

Now that it is all installed, I am still dealing with hangs.  During install with the live cd, the hangs seemed random; sometimes it would get all the way into the live cd and freeze before step three of the install, sometimes I wouldn't et to the desktop, etc.

Now that it is installed, the hangs no longer seem random.  I can always log in, I can do simple things, like load up a game.  As soon as I try to launch Synaptec or even a terminal....hang.  Time after time this happens.

System Info
----------------
CPU=Intel P4 3.6Ghz with hyper-threading
RAM=4GB
Video Card=ATI Radeon 9700 Pro
Sound Card=Sound Blaster Audigy2 ZS Platinum

I have already run the memtest, and came up with 0 errors. I'm not sure where to go from here.  I have 0 problems with this box running winblows. :mad:

Any thoughts?

---

### Post by raffytaffy on 2008-02-07
Is all the ram the same type?

---

### Post by agentno4 on 2008-02-08
Yes, all of the RAM is identical.

---

### Post by agentno4 on 2008-02-08
Oh, forgot to mention before, not that it should change anything, my cpu is 64-bit and I am using the 64-bit version of Ubuntu.

---

### Post by PmDematagoda on 2008-02-08
How did you setup your VGA card? Sometimes it could be some improperly setup hardware causing the problem.

---

### Post by agentno4 on 2008-02-08
The VGA card was set up automatically during install.  I did dig though the xorg.conf, to ensure that it was loading the ati driver, which it was.  It seems unlikely that hardware is an issue, since it always lets me log in, takes me to the desktop, etc.  So far, the only thing that I have tried to do which causes the hang is attempted to open a terminal and open the update manager.  I will do some more playing to see if I can get it to hang while doing other things.

***Scratch that. I managed to get it to crash opening other programs.  Sometimes I can open games, sometimes I can't.  So far I have not had a problem opening folders and such.  EVERY time I try to load a terminal it hangs.

---

