---
title: "Moving to 64bit, not sure about old configs and..."
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Darkshade on 2009-04-17
[COLOR="DimGray"]Hello,
I finally decided to move from 32 to 64bit but I'm not sure about a couple of things. My /home is on a separate ext3 partition that I'll keep intact.

What I'm not sure about is if I can keep my old configuration files and folders (the hidden stuff in my Home) or it will conflict in some way with the new 64bit install? The only files I'll actually need are from Exaile and Firefox. I don't mind resetting everything else to default, actually I kinda prefer to do it :)[/COLOR]

Long story short - should I delete my old config files before I reinstall or they won't be a problem?

Also, how stable is ext4 at the moment (I'm talking about the data loss problems) and is it really worth using it for / ?

---

### Post by NewDisciple on 2009-04-17
**The first time I installed a 64bit system I didn't remove the old config files which caused endless problems, so I would say yes, remove them.  I have ext4 and like it.  Supposed to be faster...  However, having ext3 and ext4 on the same system would be a problem.  If you want ext4, backup your home files to disc or external harddrive and reformat your home partition.**

---

### Post by James_Lochhead on 2009-04-17
Yea I have had problems with config files as well. I suggest you use Del.ic.ious or foxmarks for your bookmarks for Firefox (if that is what you mean) in the future. They you can get them back whever. 

As for ext4. Lots of people say it is fine, however, I have had problems with my computer freezing that I think are ext4 related (since I now use ext3). The speed is vastly exaggerated. Phoronix did benchmarks and real life tests and the speed is basically the same (give or take)...

---

### Post by FuturePilot on 2009-04-18
Config files shouldn't cause any problems between architectures. They're just text. The only thing that would be a problem are any binaries. I just switched to 64bit as well and I left my /home just the way it was. No problems.

---

### Post by Darkshade on 2009-04-18
Thank you all for replying, although I didn't see them until I just finished installing - I was kind of in a hurry, sorry about that.

Anyway - what I did was move all my config files to another folder just in case and now that everything runs smooth just I'll put the ones I need back.

Installed Jaunty RC 64bit on a ext4 / partition and kept my /home ext3 (if everything works ok with ext4 I'll format my home too, but for now I don't want to risk it). Then added the 2.6.30-RC2 kernel (who doesn't like to play with a fresh, recently installed distro? :D ) and I still can't believe this is real - it's running faster than ever! Restarted 3 times to check my boot speed and I got 14, 15 and 14 seconds again on my old 1.8ghz Sempron (used to take about 25-28 with the stable 2.6.28.11, 32bit and ext3), thought booting isn't the only thing that's faster than before - the desktop itself really feels lighter and faster too, and I was already using Jaunty since early alphas but it never felt so good :D

---

