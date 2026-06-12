---
title: "Video glitches with radeon 9600 (alpha5)"
date: 2008-09-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by thegcat on 2008-09-07
Hello,

I have installed 8.10a5 on a desktop with a Radeon 9600 (reported as RV350 AR by lshw) a few days ago, and I have glitches in overlaid videos (totem as well as mplayer). I haven't used linux with an ATI card for a long time, anything I should be aware of, or any tips for me to correct these glitches.

Thanks :-)

---

### Post by dupondje on 2008-09-08
maby u have same as me
check: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/267612](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/267612)

---

### Post by thegcat on 2008-09-08
That did it, merci beaucoup :-)

Still, I'd very much like to know the cause of the problem, not how to cure the symptoms. If I read the dupe of your Bug correctly, it would be a problem with DMA on these cards, or at least the implementation of DMA in the drivers, and that would be a bug that should get forwarded up to the xorg-radeon people.

---

### Post by BwackNinja on 2008-09-08
I'd say the bug is that EXA isn't default for whatever reason not that there are green lines. EXA is now better than XAA for radeon and supports full composite unlike how it used to be. I wouldn't expect this to be fixed considering that it would be working on the old 2D acceleration architecture rather than the newer, faster one. I see no reason for EXA not being the default though.

---

### Post by thegcat on 2008-09-09
OK, I just read what EXA and XAA are :-) Anyway, and as I said earlier, I've been a little out of the loop for the past months, how far is X.org in [strike]steroids[/strike] full OpenGL?

> **BwackNinja said:**
> I'd say the bug is that EXA isn't default for whatever reason not that there are green lines. EXA is now better than XAA for radeon and supports full composite unlike how it used to be. I wouldn't expect this to be fixed considering that it would be working on the old 2D acceleration architecture rather than the newer, faster one. I see no reason for EXA not being the default though.

So either EXA is stable enough to be made default for all xorg-radeon-driver supported cards (at least) and should be made default in Ibex, or XAA needs to be fixed nonetheless, else you'll have loads of people complaining about green lines in their overlays and a big part of them without competence or motivation to go add this one line in the xorg.conf. Hope this gets fixed in the next release :-)

---

