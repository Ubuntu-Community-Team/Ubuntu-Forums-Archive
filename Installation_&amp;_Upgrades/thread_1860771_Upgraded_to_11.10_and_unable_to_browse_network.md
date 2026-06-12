---
title: "Upgraded to 11.10 and unable to browse network"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by Kevin Kent on 2011-10-15
Updated 3 machines now from 11.04 to 11.10 which were all successfully navigating network to NAS. Now Nautilus starts but is slow to browse network. Once device displayed Nautilus slows and then errors with "Unable to mount location  - failed to retrieve share list from server".  Any clues as to what needs to be tweaked?

---

### Post by dino99 on 2011-10-15
try:

sudo dpkg-reconfigure -phigh -a

---

### Post by Kevin Kent on 2011-10-15
Thanks for advice.  Ran it, rebooted and no effect. Still same error.

---

### Post by bobsageek on 2011-10-16
Same error when trying to browse to my shared storage on a Cisco e4200. Can see and mount all shares from my wife's iMac, just not the network storage (which worked fine in 11.04 and from the iMac).

---

### Post by Kevin Kent on 2011-10-16
This thread has cured it for me:  [URL="http://ubuntuforums.org/showthread.php?t=1861985"]http://ubuntuforums.org/showthread.php?t=1861985
[/URL] :D

---

### Post by bobsageek on 2011-10-16
> **Kevin Kent said:**
> This thread has cured it for me:  [URL="http://ubuntuforums.org/showthread.php?t=1861985"]http://ubuntuforums.org/showthread.php?t=1861985
[/URL] :D

This solved my issue as well, thanks. :guitar:

---

