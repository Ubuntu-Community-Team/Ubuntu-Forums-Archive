---
title: "xserver gone with Edgy upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by joplass on 2006-10-27
I just upgraded to Edgy and I lost my server.  Could there be a solution for me](*,) ?
I have an ATI Radeon Mobility M6 LY card.
Thanks

---

### Post by Culito on 2006-10-27
My xserver didn't completely install.  I just had to do this:

sudo apt-get install xserver-xconf

That did the trick.

You might want to add "-driver-radeon" after xconf.

---

### Post by em es on 2006-10-27
I've got that problem too. I'm going to see if that solution works with me too.

---

### Post by crimesaucer on 2006-10-27
me too, and my xubuntu 6.10rcbeta was working perfectly untill I ruined my system trying beryl, so I had to install and upgrade again, and now I'm getting that blue text screen saying that my xserver is not configured.

---

### Post by vibestriton on 2006-10-27
Have you tried the following?

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Johnsie on 2006-10-28
I did this to fix similar problem

> 
sudo aptitude install xserver-xorg-video-savage



As you can see my card was a savage card. Doing this apt-getted the savage card driver.


**To find out what driver YOU need to apt-get:**

> 
sudo dpkg-reconfigure xserver-xorg


Do all the autodetect stuff. You will see a screen with a list of possible drivers. It is usually a list of things like nividia,nv,s3,s3 virge, savage etc. Write down the one that was selected.

Then all you need to do is apt-get the driver as shown at the top of this post only replacing "savage" with whatever driver your need.

---

### Post by em es on 2006-10-30
I tried
```
sudo apt-get install xserver-xorg
```
And after that there were absolute zero problems.;)

---

