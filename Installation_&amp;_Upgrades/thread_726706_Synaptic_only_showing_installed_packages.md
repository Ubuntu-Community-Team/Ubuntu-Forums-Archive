---
title: "Synaptic only showing installed packages"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by cineris on 2008-03-17
Ok, so my gf's computer crashed and I convinced her to go to Ubuntu finally.

Anyhow, it installed fine, no problems, and then here we are, trying to get packages that she needs/wants installed and Synaptic is only showing the packages she already has installed.  I've tried turning the CD repository off, and hitting refresh, and nothing...  and when I have the CD repository turned on, and the CD in the computer, it says that it cannot load the repository.

I know we cannot be the first ones to have run into this problem, but we cant find any solutions on the forums, we've been looking for about half an hour already.

Someone please help!!!  Thanks in advance!

Also, when we try to install flash for Firefox, it says that it cannot find it.  It almost seems like it can't connect to the source for the packages.

---

### Post by mikewhatever on 2008-03-17
Well, flash is not installed, so how did you find it? Can you open Applications>Accessories>Terminal and post the output of the following:
cat /etc/apt/sources.list.
There seems to be a similar problem here --> [http://ubuntuforums.org/showthread.php?t=726742](http://ubuntuforums.org/showthread.php?t=726742)

---

