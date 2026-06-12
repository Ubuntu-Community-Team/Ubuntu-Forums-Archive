---
title: "Major Desktop problems with 11.04"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by dbclinton on 2011-08-18
I've tried to install 11.04 (both Edubuntu and Ubuntu 32-bit) on two separate machines. In both cases - both for live session and after actual installation - the Desktop is unusable. I'll click on a menu item but the window will not appear at all, or appear only for a split second or, if I hit alt-tab, it might appear, but not all of the controls will function. Some items on the panel are also skewed. 
On the HD install, I selected to NOT install Unity, on the live sessions, I took whatever they gave me (didn't look like Unity - I've been using Unity on my netbook for some time). Same effect either way.
One machine has a 3.06 GHz processor and 2GB RAM. The Display controller is an integrated Intel 82865G and the driver is the Intel i915.
Any ideas?
Thanks,
David

---

### Post by dbclinton on 2011-08-18
It turns out (based on this thread: [http://ubuntuforums.org/showthread.php?t=1745151](http://ubuntuforums.org/showthread.php?t=1745151)) that there is a nasty conflict between 11.04 and the Intel 865g video controller. Not only did my first computer run that controller, but so did my second (an IBM ThinkCentre 8187). 
Just my luck.

---

