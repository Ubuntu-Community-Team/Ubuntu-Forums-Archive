---
title: "raid drive issues"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by Mongo5000 on 2007-07-31
Very new to linux coming from a hardcore windows xp nerd.  I've searched the forums and google to no help.  With all my tries, i've had to reinstall ubuntu about 20x times.  Not that i mind, but im tired of breaking it.

My PC setup.

2x 160gig sata drives in a raid with a silicon hardware card.  4 partitions, 3 data, 1 with winxp
1x 80 WD IDE drive with ubuntu installed.

I want to be able to load ubuntu and access the data on my raid data partitions.  I just cant get ubuntu to see the raid regardless of what i've tried.  when i do a fdisk -l it see /dev/sda and /dev/sdb but when I try to mount them, it errors.

I would REALLY like to install ubuntu on the winxp partition since I don't need winxp anymore, but during installation, ubuntu doesn't see the raid as 1 drive.  See's it as 2 160 drives.

Any suggestions?

---

### Post by Pumalite on 2007-07-31
[http://www.linuxquestions.org/questions/showthread.php?t=567935](http://www.linuxquestions.org/questions/showthread.php?t=567935)

---

### Post by Mongo5000 on 2007-08-01
I can't thank you enough.  Worked like a charm!!!!!!

---

### Post by Mongo5000 on 2007-08-01
So now that i've played with it a bit, I noticed one thing.

When I do a dmraid -ay I get this.
RAID set "sil_afabahdcajbd" already active
RAID set "sil_afabahdcajbd2" already active
RAID set "sil_afabahdcajbd3" already active
RAID set "sil_afabahdcajbd5" already active
RAID set "sil_afabahdcajbd6" already active

I see each one of those is my different partitions but when I try to mount each one, it just changes the initial mount so I can't mount each one at the same time, its one or the other.

Is that possible to mount each one at the same time?

---

### Post by Mongo5000 on 2007-08-02
Still looking for help with this.  I read through the docs on dmraid but still can't get it working.

---

### Post by Pumalite on 2007-08-02
Sorry, but I'm not a Raid guy.

---

