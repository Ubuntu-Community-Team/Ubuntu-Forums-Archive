---
title: "Low resolution in Ubuntu 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by ladavis89 on 2010-05-01
Hardware:

nvidia Geforce 8600 GT
Samsung SyncMaster 216BW

I upgraded to 10.04 and when I rebooted, the screen resolution was at 800x600 with no higher options.  I installed the latest nvidia driver through the hardware drivers application and when I rebooted, the screen went black with the backlight still on. 

Then I have to reboot into one of the other ubuntu kernels and an error appears saying:

(EE) NVidia: failed to load kernal module
(EE) failed to load module 'nvidia' 
(EE) no drivers available

After this, it puts me back to low grahics mode and I am back where I started....

I have blacklisted noveau in blacklist.conf file also.  

 Could someone point me in the right direction with this graphics problem? I have been working for about 14 hours straight on getting 10.04 working properly and this seems to be the last thing i have to do...


BTW, I had to use nomodeset to boot into the latest ubuntu kernel.  


I appreciate any help!!

---

### Post by ladavis89 on 2010-05-01
Is there anyone that can help me?

---

### Post by chappajar on 2010-05-01
Possibly here: [http://ubuntuforums.org/showthread.php?t=1346125](http://ubuntuforums.org/showthread.php?t=1346125)

---

### Post by ladavis89 on 2010-05-02
No that didn't work either...It won't recognize those resolutions.  I really am at a loss of what to do here...

For now I am going back to 9.10 until 10.04 decides it wants to work correctly.

---

### Post by missdanish on 2011-01-05
Hi!

Cheers for that :)  I had the same issue but for some reason the file I needed to edit was called "yelp" 

(~/.gnome2/yelp)

the file contents were:

[Geometry]
width=600
height=420

but changing the width and height to 1024 and 768 fixed it for me!

---

