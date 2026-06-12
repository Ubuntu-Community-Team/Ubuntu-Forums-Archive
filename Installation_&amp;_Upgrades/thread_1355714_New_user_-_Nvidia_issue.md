---
title: "New user - Nvidia issue"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by ebaker on 2009-12-15
I was turned on to Ubuntu from a fellow co-worker and have little experience with Linux based systems. I am just so tired of all the baggage that comes along with XP on a couple of older machines I have that I would really like to make this work.
 
The system is a Dell Precision 530 with dual Xeon 1.5GHz processors, a 17GB SCSI, 256M ram, and an Nvidia Quadro2 Pro video card.
 
I had set up a dual boot with XP then Ubuntu this weekend and everything seemed to be working. However, we tried to load a simple kids game on the XP system and somehow I was bumped in to low resolution mode when returning to Ubuntu. Coincidence?
 
I wiped the drive and reinstalled Ubuntu 9.1 and am still stuck in low res mode with a max of 1024x768 on a 21" monitor. I had to modify the Xorg.conf to get there adding the horizontal and vertical refresh rates.
 
I also tried installing the Ubuntu Nvidia video drivers (versions 96, 173, 185) with no luck. Is this more likely a hardware issue? It worked on initial installation with options of much higher resolutions. Making my way around a terminal is a little slow right now as I am on the bottom of the learning curve.
 
Thanks for any help here and I apologize for asking for help on the first post.
 
Eric

---

### Post by egravede on 2009-12-16
Try installing the drivers with EnvyNG (quick google search).  Most of the times, especially with video cards (I know this from experience :]), Ubuntu fails badly at installing the drivers itself.  I've used Envy on 4 other Linux boxes at my work and so far everything is working great.

---

### Post by ebaker on 2009-12-22
Thanks, I did actually try EnvyNG and it could not find a compatible driver after which I knew I was in trouble.  I wound up building my own Xorg.conf using the built in nv driver.  I just wish I could enable openGL in hardware.  glxgears yields only 630 frames in 5.0 seconds.  I may have to get a cheap upgrade card.

Here is the thread I posted regarding the "fix".

[http://ubuntuforums.org/showthread.php?t=1362156](http://ubuntuforums.org/showthread.php?t=1362156)

---

