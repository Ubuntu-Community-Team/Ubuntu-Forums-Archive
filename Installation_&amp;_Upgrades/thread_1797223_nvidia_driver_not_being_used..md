---
title: "nvidia driver not being used."
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2011-07-04
Hi,

I just upgraded to 11.04 a couple days ago, and it didn't go smoothly because I ran out of space, so I had to pause it and grow a partition.

When I got done there were several problems.  One of them is that my nvidia proprietary driver is no longer being used.  I found it in "additional drivers" and activated it, but it says "no proprietary drivers are in use on this system.  This driver is activated but not currently in use."

I can run the nvidia control panel just fine, and write an xorg.conf file, but after I reboot the above message stays the same.

My xorg.conf file says to use the nvidia driver.  My Xorg.0.log shows the nvidia board coming up what seems to be normally.  

Is there something obvious I'm missing?  The "appearance" control panel doesn't even have the special effects tab anymore.

Thanks.

---

### Post by mörgæs on 2011-07-05
There are many threads on this error message, for example
[http://ubuntuforums.org/showthread.php?t=1743386](http://ubuntuforums.org/showthread.php?t=1743386)

---

### Post by Frogs Hair on 2011-07-05
There are many bug reports filed for this problem . If you are able to use 3d effects the driver is in use . 
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

---

