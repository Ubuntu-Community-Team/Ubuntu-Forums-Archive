---
title: "RAID 1 w/ System Drive nad How To Connect IDE Hard Drives Question"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by blueorder on 2007-08-28
I've been contemplating moving my Windows server to 7.04 server. I am currently running the Windows server with 1 system drive and 2 drives on RAID1 through an Adaptec 1200A card.

When I move to Ubuntu I will remove the 1200A card and setup with a system drive and the 2 drives in software RAID1.

My question is, with all 3 drives being IDE, what will be the most efficient (read optimized) way to connect the 3 drives and CDROM (I can disconnect CD after install) into the 2 IDE connections?

---

### Post by monkster on 2007-08-30
If you are going to ditch the Adaptec card, the best thing to do is to get another ide controller. For s/w raid, you want to run all your hard drives as master; master/slave drives for linux s/w raid will have problems. HIghpoint or Silicon Image controllers are cheap and will work fine for this. You might want to run a system hard drive from the system board ide connector and the raid1 array off the ide controller card. That would be pretty simple, but you have other options, of course.

---

### Post by blueorder on 2007-08-30
Could I use the Adaptec 1200A as the IDE controller, just not use the RAID capabilities?

---

