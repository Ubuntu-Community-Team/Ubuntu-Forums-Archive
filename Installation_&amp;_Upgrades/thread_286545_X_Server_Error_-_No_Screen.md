---
title: "X Server Error - No Screen"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Pata-kun on 2006-10-27
Hey everyone, I hope someone can help me.

I was upgrading from Dapper to Edgy today.  Everything was going fine, I restarted when prompted, and Upstart showed up fine.  After that though, the screen flashes a few times.  Then it states X Server Fatal Error: No Screen Found.

I've checked through the threads here, reconfigured X, nadda.  Nothing so far seems to help :(  Anyone have any ideas how I can fix this?

---

### Post by viper on 2006-10-28
[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)
Check this thread out.:)

---

### Post by Johnsie on 2006-10-28
I had the same problem that the poster of this topic had... It was very easy to fix:

> 
sudo aptitude install xserver-xorg-video-savage



As you can see my card was a savage card. Doing this apt-getted the savage card driver.


**To find out what driver YOU need to apt-get:**

> 
sudo dpkg-reconfigure xserver-xorg


Do all the autodetect stuff. You will see a screen with a list of possible drivers. It is usually a list of things like nividia,nv,s3,s3 virge, savage etc. Write down the one that was selected.

Then all you need to do is apt-get the driver as shown at the top of this post only replacing "savage" with whatever driver your need.

---

### Post by Pata-kun on 2006-10-28
Alright, I'm attempt to apt-get my nvidia card, but then this appears when I attempt to install:

> Media Change: Please insert the disc labeled 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)' in the drive '/cdrom/' and press enter

But, when I put in my 10.6 LiveCD and press enter, it won't accept it; just displays the same message over and over.  Where am I suposed to get this mystery disc? :P

---

### Post by Pata-kun on 2006-10-28
Does no one know what I have to do? :(  I'll bake you e-cookies if you help me...?

---

### Post by nbx909 on 2006-10-28
use nano to remove the cdrom part in your apt sources.list

---

