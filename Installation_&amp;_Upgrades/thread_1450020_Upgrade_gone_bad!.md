---
title: "Upgrade gone bad!"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by mjmcomputer on 2010-04-08
Hello everyone. I have used and installed Ubuntu in the past but am now having problems with upgrading a clients PC.
It is an eMachine, Celeron 2.5GHz, 512 MB RAM, Via KM400, 40GB HDD.
It was running 7.10 Gutsy Gibbon. He wanted to upgrade and use a Cricket UM185C wireless modem. After searching the forum for info on this modem it appeared that he would be better off running 9.10 Karmic Koala so I started to upgrade him. I was able to upgrade to 8.04 Hardy Heron without issue. When I tried the next upgrade to 8.10 Intrepid Ibex everything seemed to be going fine until restart. Now I get the folowing message:
> Ubuntu is running in low-graphics mode
The following error was encountered. You may need
to update your configuration to solve this.
(EE) CHROME(0): No valid modes found
(EE) Screen(s) found but none have a usable configuration.
When I click OK I get a box asking me what I want to do?
> Run Ubuntu in low-graphics mode for just this session
Reconfigure graphics
Troubleshoot the error 
None of the options get me to the desktop.
I then thought maybe I'd try a fresh install of 9.10 but when I boot the live CD I eventualy come to a point where the screen is full of text and blinking on and off and the ubuntu@ubuntu:~$ prompt is at the bottom.
Any help is appreciated.:confused:

---

### Post by solar george on 2010-04-08
Just a guess but does that machine have Via Chrome graphics by any chance? From what I've heard they're nothing but trouble maybe you'd be better off fitting a new fairly basic ati/nvidia graphics card.

---

### Post by mjmcomputer on 2010-04-08
Yes it is the onboard video from VIA. It boots the 7.04 live CD just fine but not my 9.04 or 9.10 I might have and old Nvidia card I can try.

---

### Post by mjmcomputer on 2010-04-08
I put in an old Dell Nvidia card and it booted fine. I'm still going to do a fresh install of 9.10 as it will be quicker than upgrading.

---

