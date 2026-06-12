---
title: "Family Partitions"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by danbar on 2010-01-05
I wish to create several partitions on my PC as it's going to be shared by various family members. I opt for partitions (instead of using just several users and creating the corresponding number of homes), because the normal home is too small. A partition is more secure for users so as not to touch the system and especially if the system goes down, their files are safe.

When I try to create partitions during installation I'm finding several problems with Ubuntu 9.10. I have to mount each partition on a particular point (and no point can be used for two different partitions). I know it has to be extended in order to create more partitions.

I tried to do just one big partition (besides that for swap and for the system) and then after installation tried to use gparted, but as the mounting point was home, it won't allow me to resize it or create new partitions.

When I put it in /boot it screwed up the booting file. Now the other alternatives are /tmp and /var did not work well. ([http://ubuntuforums.org/showthread.p...hlight=gparted](http://ubuntuforums.org/showthread.p...hlight=gparted))

Any ideas? Thanks for your time and patience.

---

### Post by fatbotgw on 2010-01-05
It is my understanding that if you set a separate partition as your /home then you can only do that once...

If you're worried about being secure then why don't you encrypt the /home folders for the users?  I believe there's an option for that on install...

---

### Post by jose07 on 2010-01-06
If you are getting a resize error, because you have to unmount the media first, you could try to use the Live Cd, and do it from there. Otherwise, use the Logical Volume Manager to create more volumes, and size them to how you see fit. As far as losing data, your data is still there, you can use the Live Cd again, and look at it. If you have several hard drives you could point there home directory to that drive. Good luck.

---

### Post by danbar on 2010-01-06
Thanks for your feedback!

---

