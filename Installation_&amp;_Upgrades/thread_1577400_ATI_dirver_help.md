---
title: "ATI dirver help"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by dirt_diver on 2010-09-18
Hello,

First off I hope that I have posted this in the right place.

I am trying to convert to Ubuntu, downloaded 10.04 64-bit and installed it. The graphics were kind of sluggish and I was not able to adjust them in the System-> Preferences-> Appearance-> Visualization area, when I try to choose extra option it tries to look for drivers and fails. I have looked in many places on how to install the ATI proprietary and open drivers with no luck.

These are the guieds that i have followed so far:

[https://help.ubuntu.com/community/RadeonHD]("https://help.ubuntu.com/community/RadeonHD")

[http://ubuntuforums.org/showthread.php?t=1456282]("http://ubuntuforums.org/showthread.php?t=1456282")


TY for any help you've got

---

### Post by goodolandy on 2010-09-18
Did you try going to System -> Administration -> Hardware Drivers to see if Ubuntu gives you a proprietary driver to activate?

That's what I did for my system which is using a ATI HD4350 card.  The Catalyst is now 2 versions out of date but I have full desktop effects on with dual display.  Only thing I am unable to do is play my Windows games in full screen mode without my second display becoming disabled.

---

### Post by dirt_diver on 2010-09-19
Yes I have went there and it did list a ATI driver there but the install would never complete, thats when I went to the ati website and downloaded the deb from there. When sh that file it would work to a point where the ATI installer says that it is complete but in the terminal window I get an error with DKMS. After using that package when I go to the System -> Administration -> Hardware Drivers no ATI driver is there...

I also should note I am running 2 5870's, should I pull one of them out of my system then try this again?

---

### Post by dirt_diver on 2010-09-19
Got it fixed, followed: 

> Re: FGLRX wont install
I also stumbled upon the same problem today..
So what I ended up doing was:

1) removed the 32-24 kernel:
Code:
sudo apt-get remove --purge linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
2) removed the manually installed, but broken fglrx drivers:
Code:
sudo apt-get remove --purge fglrx fglrx-amdcccle fglrx-dev
3) installed the old kernel:
Code:
sudo apt-get install linux-headers-2.6.32-23 linux-headers-2.6.32-23-generic
4) installed fglrx from the repos (which installed with no problem on 32-23):
Code:
sudo apt-get install fglrx fglrx-amdcccle fglrx-dev
5) and finally, activated the proprietary drivers from "hardware drivers" and rebooted

This works fine, but not under 32-24, cause as soon as I install linux-headers-2.6.32-24 and boot into it, the proprietary drivers get broken again. So I guess I'll just have to wait until they fix the compilation bug under 32-24

Hope it helps.

Regards,
progre55

---

