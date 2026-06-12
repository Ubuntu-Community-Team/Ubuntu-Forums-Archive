---
title: "Saving some Windows stuff."
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by LinXNut on 2013-06-22
Hey guys! I really want to install Ubuntu back onto my computer, but the only thing that is holding me back is...I'm a gamer. Yes, I play World of Warcraft and a couple other games as well. I have read online and have seen that most of the games I play work perfectly fine with Ubuntu. Here's my question:

-Can I partition a part of the hard drive and move all the games I own to that partition, so when I install Ubuntu I can run them via wine instead of re-installing them completely?

Basically I want to move all my games to a separate part of the hard drive so I can install Ubuntu, but keep my games. I was wondering if this is possible?

Thanks!

---

### Post by dino99 on 2013-06-22
with linux (ubuntu) there are a few partitions : / (root for the system), swap (the swap partition) and /home (where your data/settings/apps/games/... are)
by the way its better to do a clean reinstall of these games

[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by Mark Phelps on 2013-06-22
> **LinXNut said:**
> Can I partition a part of the hard drive and move all the games I own to that partition, so when I install Ubuntu I can run them via wine instead of re-installing them completely?

Basically -- NO.  Games are apps, after all, and in Windows, pieces of apps get installed in a variety of different directories, not to mention through the "registry" (which is really a collection of files).  There's no way to "move" an app to another partition.

And, playing Windows games through Wine is an entirely different process than playing them natively in Windows.  One of the major differences is that in Windows, you're using Windows video drivers -- which generally provide good hardware acceleration and DirectX support, but in Wine, you're using Linux drivers -- which is a whole different situation.

Your best best is to retain Windows on the PC and run the Windows games there.

---

### Post by LinXNut on 2013-06-22
Thank you for the quick replies! And yes I agree windows' games run best on a windows OS. I could always try dual-boot (which I'm not a fan of)? I could use dual boot to "test" and see if it works.

---

