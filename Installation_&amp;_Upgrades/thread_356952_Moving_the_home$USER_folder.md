---
title: "Moving the /home/$USER folder"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by mlissner on 2007-02-09
I'm trying to set up a somewhat seamless dual-boot machine with a shared partition working between Ubuntu and XP. I've got that all set up OK, and operating OK, but I want /home/$USER to point to the shared partition (/media/hdc4).

As it is, to save things in the partition is a pain in the butt, and I don't like it. Any thoughts on the subject out there? 

I'd like to just make a symbolic link so that /home is just redirected where it needs to go, but I'm scared things will go nuts.

Thoughts?

PS - I tried to set up a /home partition when installing, but the installer stonewalled me with a strange error unless I made it ext3, which I did at first, but then XP wouldn't talk ext3, so I had to change the shared partition to FAT32, and NOT make it /home.

---

### Post by aysiu on 2007-02-09
/home/username has some pretty delicate permissions. I would not make it FAT32.

Your best bet is to use [http://www.fs-driver.org](http://www.fs-driver.org) to read/write an Ext3 partition (/home/username) from XP.

---

### Post by mlissner on 2007-02-09
Yeah, that looked good, and I tried it, but it didn't work at all, totally froze things up, and so it made sense to use a format that's native to both OS's. 

I'm not a huge advocate for putting /home/$USER on there in actuality, but I would like it to seem like it's on there via a link or something...

---

