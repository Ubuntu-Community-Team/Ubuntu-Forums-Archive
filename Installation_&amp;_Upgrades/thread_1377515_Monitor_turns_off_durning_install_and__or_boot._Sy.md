---
title: "Monitor turns off durning install and / or boot. System hang."
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by Bryan Horton on 2010-01-10
I need help. I am brand new to any type of linux. I have been trying out the ubuntu 9.10 and I am having trouble getting it to run on one of my home systems.
 
To start, I have am unable to get it to boot off the live CD. It goes so far and then the monitor turns off as if it goes into power save mode. Yet it is more than just the monitor, the whole system appears to hang because from then on, if I press any keys on the keyboard such as numlock, the light will not toggle off and on on the keyboard.
 
The funny thing is, one time, it did boot off the live CD (perhaps 1 out of 30 tries). When this happened, I went ahead and installed it. After the install completed, I have never once been able to boot. The same hang keeps occurring with the system. I have also not been able to boot into the live CD again.
 
I spent about four hours working this yesterday and tried all sorts of things I was reading the forums, but nothing seemed to help. I am thinking it has to do with video resolution but I don't know for sure. 
I have an AIT Technologies Inc RV670 Pro Radeon HD 3850 card.
 
The other problem I have is that since I did all the work yesterday trying to fix it, now I cannot boot Windows. If I choose it in the GNUB menu, I get some sort of not found error. When I press a key, I go back to the GRUB menu.
 
Please help.

---

### Post by SecretCode on 2010-01-11
The CD may have errors (which may not be a problem for reading as a data CD, but could stop it working as a boot CD). If you can, check the download has the right MD5sum (see [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)) and burn a new copy at the lowest possible speed your burning software will allow.

The monitor can power off during installation. In case this is causing a problem with it waking up, move the mouse every 4-5 minutes (I don't want to bore you - this is just an idea).

By the way, it's GRUB not GNUB. :)

---

