---
title: "Updated...graphics issue"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by threequarterthrottle on 2010-12-28
Hello.  I'm running Ubuntu Studio 10.10 on an Emachines(don't laugh, it was a trade acquisition and it's been the most reliable system I've ever owned) W3623.  It's an older system, I've also used 10.04 with no issues.

   Anyhow, I mindlessly OK'd the update manager this morning on cup #1 of coffee, and everything was cool.  It requested a reboot, I obliged.  When my system came back on, my monitor was in severe misalignment.  No big deal, I decided I must have updated a graphics driver my system didn't like.  I'm running the factory Intel GMA 950, according to the sticker on the front of the tower.  according to terminal:

joe@Home:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

The monitor is an Emachines E17T4W TFT LCD, if it's helpful.

I went to the UD manager, and I can't find any sort of history on what I updated.  Nothing in package manager(of course, I didn't use package manager this time).

I also looked in the System>Administration>Additional Drivers, found nothing helpful.

I'm a pretty capable windows user, but I'm new to Ubuntu/linux.  I've read about compiling drivers and installing them, but I don't quite feel comfortable tackling that.  I considered reinstalling the OS, but there has to be an easier way.

I can't adjust the monitor enough to get it all in there, my left side hangs off the end.

P.S: I've read a few threads about that particular graphics card, and it's not as bad as many think.  I run OpenArena flawlessly at 1024x768, haven't tried it any higher.  It's not like my precision m4400, but it's fair.

Thanks in advance for any help, and please keep in mind I'm a timber cutter, not a computer guru.  I can follow instructions, but I'm still a little lost in the land of penguins.

---

### Post by threequarterthrottle on 2010-12-28
Update:  If you run a program that changes the monitor resolution, it centers properly.  once the computer hibernates again, it goes off-center.  I dunno, thanks!

---

