---
title: "after upgrade must give password to use usb or dvd"
date: 2015-11-08
forum: Installation &amp; Upgrades
---

### Post by uh-huh on 2015-11-08
Youtube-dl complained that avconv was out of date. Update avconv failed because of an issue with the "key". Long story short went here and followed the instructions [http://deb.opera.com/manual.html ]("http://deb.opera.com/manual.html")I don't know what opera had to do with it. But that's what it took.

Everything was fine after that except now I have to enter my password to read a USB stick or watch a DVD. But my /media/<username> ownership hasn't changed.

How do I put it back the way it was?

---

### Post by uh-huh on 2015-11-09
Here I go replying to my own thread. This thing is SOL-VED! I rebooted; all is cool

---

### Post by yancek on 2015-11-09
> I don't know what opera had to do with it. 


Probably nothing.  The apt-get update probably did though.

---

### Post by Dennis N on 2015-11-10
I think that upgrading Policy Kit files will cause temporary permissions problems with udisks until you either 1) log out and in, or 2) reboot the computer. I have seen the same (again) just recently.

---

