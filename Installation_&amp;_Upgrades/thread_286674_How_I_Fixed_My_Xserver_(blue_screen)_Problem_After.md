---
title: "How I Fixed My Xserver (blue screen) Problem After Upgrading"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Johnsie on 2006-10-28
It was very easy to fix:

> 
sudo aptitude install xserver-xorg-video-savage



As you can see my card was a savage card. Doing this apt-getted the savage card driver. Replace the word "savage" with whatever driver you need to install.


**To find out what driver YOU need to apt-get:**

> 
sudo dpkg-reconfigure xserver-xorg


Do all the autodetect stuff. You will see a screen with a list of possible drivers. It is usually a list of things like nividia,nv,s3,s3 virge, savage etc. Write down the one that was selected.

Then all you need to do is apt-get the driver as shown at the top of this post only replacing "savage" with whatever driver your need.

---

