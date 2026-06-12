---
title: "Not enough room in root during 12.10 upgrade"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by stroudwaterboy on 2012-10-21
Sorry my first post is asking for help!
 
During the 12.10 upgrade I had a failure saying that there was insufficent room in root, not unusual I always take all the updates and after a couple of Linux updates get this. I have a procedure to deal with it using some comands in terminal.
 
The problem I have is that I couldn't get out of the prcess giving the error message it just kept cycling around, I couldn't run my normal process as it said another routine had control! The same with Synaptic.
 
In the end I gave up and created a live CD, can boot from this fine but no matter what I try I can not get rid of the extra files in Root. Tried booting normally but it goes to Grub Resue and I can't seem to get any of the advice here working for that either.
 
I expect that this is dealt with already on the forum but I cannot find the right search to get to it.
 
Help, please.

Have managed to solve this myself sort of.

Found a reference else where to using Nautilus by using gksudo natilus, I could then use this to delete the extra files in root, not sure this is totally desirable as you could delete important file but it made room.

I then ran boot-repair that I found details for and I now have a machine I can use although I am not happy with the way it is working I can at least use it now.

---

