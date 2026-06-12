---
title: "Some questions"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by djw on 2006-07-02
Ok Well I'm extreamly new to the linux world so bear with me...  Well when I installed XP on my 200 Gig HD it partitioned all but 58 gigs which I recently remembered.  Now I'm just checking on this, but I could install Ubuntu on that 58 gigs without bothering my XP stuff, correct?  If you have any other advice on the partitioning of that 58 gigs just let me know.  Thanks for all the help.

---

### Post by christhemonkey on 2006-07-02
Yes installing to that 58 gigs of space shouldnt be a problem.

Just remember during the install, to select manually partition hard drive.

Then create a swap partition and a 57(ish)gb partition for the rest of the space.

(swap partition should be 2 x RAM size)

---

### Post by Zimmer on 2006-07-02
[QUOTE=christhemonkey]Yes installing to that 58 gigs of space shouldnt be a problem.

Just remember during the install, to select manually partition hard drive.

Then create a swap partition and a 57(ish)gb partition for the rest of the space.

(swap partition should be 2 x RAM size)[/QUOTE]


Have a read here for examples
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by djw on 2006-07-02
One more question I have, I have yet to try the livecd but will Ubuntu recognize my wireless network card right away or will I have to find some drivers?

---

### Post by rcarring on 2006-07-02
It is doubtful that wifi will work out of the box. 

Unfortunately I can't suggest a course of action as I don't use wifi.

My comment is predicated on reading several other threads dealing with issues arising out of wifi configuration.

---

### Post by djw on 2006-07-02
That's what I thought the answer would be.  I'll look around this forum and see if I can find any other topics.

---

### Post by rcarring on 2006-07-02
I would also check the wiki as there maybe a readme or how to already neatly laid out.

---

### Post by djw on 2006-07-02
Well it looks like I have one of the hardest to get working wifi cards just by looking at other posts (F5D7001 with BCM4306 chipset).  I will look at the wiki see if there is anything else there.

---

### Post by Lin-X on 2006-07-02
I strongly suggest that you prepare your partitions before you start the installer. Use whatever disk partition program you have --- Partition Magic, QTParted, even the tool included in the live cd. Make a swap area about twice the size of your ram, and a larger area for the root file system. Then start the installer. When you get to the partition part of the install, all you will have to do is indicate to the installer which partition you want to use for what.
Partitioning from inside the installer seems not to work too well. I had a terrible time with it, and if you search this forum, you will see that lots of other people did too.

I'm amazed that you haven't looked at the live cd yet! It's awesome! It's so fast that I played with it for over an hour and almost forgot that it wasn't really installed yet. It will not hurt your computer or affect your installed system at all.
You will find the partition tool at System-Administration menu, from the menu bar at the top of the desktop. Good luck.

---

### Post by djw on 2006-07-02
Thanks for your advices I will do that.  My only worry is that I have never used linux before and it seems my wifi card is hard to config.  When making the swap area is there some special option I have to choose to make it a swap area or is it automatic?

---

