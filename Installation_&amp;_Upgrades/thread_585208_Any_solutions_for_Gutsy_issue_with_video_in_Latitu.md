---
title: "Any solutions for Gutsy issue with video in Latitute C840?"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by pnosko on 2007-10-21
Maybe I didn't ask nicely enough?  Explanation of problem is in this thread below.

[http://ubuntuforums.org/showthread.php?t=580585&highlight=C840](http://ubuntuforums.org/showthread.php?t=580585&highlight=C840)

Anyone with his model laptop NOT have this issue?

---

### Post by pnosko on 2007-12-01
Has anyone at all with a Latitute C840 got Gutsy working without video issues?  Please?

---

### Post by Army Linux on 2007-12-02
Hey Brethren

New to Gutsy. But I got my C840 running 7.10 just fine. I initially ran the livecd into safe graphics mode. But when I went through the install to hard disk, and I rebooted after taking livecd out, it is working fine. Also, by some miracle evidently,  I have my Netgear WG511v2 wireless pcmcia (Marvell Libertas chipset) working great on this same laptop.

I would use caution after install about the proprietary nvidia install w/ restricted drivers manager. i did that and jacked up the video.  I am working now with generic vesa driver, and everything is working fine. The 1024x768 is my max res right now, but I can live with that for the time being. 

Good luck.

---

### Post by pnosko on 2007-12-02
Hey Brethren, thanks so much for the reply and your tips.

I had given it another shot in the wee hours of the morning, and since I had video working on the live-boot, I held my breath and ran the install.  The laptop hung on reboot, twice, so on a whim I pulled out my Linksys WPC11 v3 card, and was able to boot successfully and video was working.  

Then, when I wanted to turn on 3D via extra visual effects, nvidia drivers (yes, the proprietary restricted ones) were installed, I hit a blank screen on reboot again (not the same scenario as before, but something that happened to me also with Feisty).

I found and followed sabi's steps in [http://ubuntuforums.org/showthread.php?t=392620](http://ubuntuforums.org/showthread.php?t=392620), and I am now in business.  :)

On an unrelated note, being able to access PCs on my Windows domain (active directory) and vise versa was not a clearly defined process, but I got that working quicker and more successfully than any other Linux I've ever tried.

---

