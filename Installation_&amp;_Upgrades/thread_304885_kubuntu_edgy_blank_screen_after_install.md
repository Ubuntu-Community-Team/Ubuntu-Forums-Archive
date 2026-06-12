---
title: "kubuntu edgy blank screen after install"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by kebajonathan on 2006-11-22
Hi guys,

I know this has been posted already many times, but none of the solutions worked for me.I don't know where to start exactly, so I'll try to report everything:

I decided to install edgy a few days ago and I did  a fresh install, expecting it would work just as some beta did. It doesn't! After it has booted, the kubuntu startup theme disappears (probably because of X.org starting) and the screen keeps black. Not entirely black, it's not switched off, but blank.

I did a fresh installation of some beta version in the 2nd week of october, where X.org worked. It had some other edges...
Yesterday, I installed edgy from the desktop CD, which worked, but after the reboot, the problem reported above occured. I tried to switch to console (Ctrl+Alt+F1-F6), which didn't work. After having booted into the recovery mode, I tried editing xorg.conf, but that made everything worse.
So today I have installed it using the alternate CD. I have exactly the same problem.

Although I don't think this is related to the machine itself, here are the specs:
IBM Thinkpad T22, video: savage IX, CPU: 900MHz, RAM: 512MB.

Do you know how to solve this problem? I need this PC.

THX in advance
Keba

---

### Post by awbassett on 2006-11-22
I've had this problem on all T20 and T22's we have at work. What I do is: 

dpkg-reconfigure xserver-xorg

Answer all the questions (I generally select the defaults) and reboot. I dont know if we have the same cause, but I HTH.

Andrew Bassett

---

### Post by kebajonathan on 2006-11-23
could you post a xorg.conf file? It would be so much easier for me since I have a lot of work to do... THX

---

### Post by awbassett on 2006-11-23
Sorry I'm not at work right now, but it really doesn't take that long.

---

### Post by kebajonathan on 2006-11-25
Seems to be a Thinkpad T20, T21 and T22 problem. I'm trying
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21)
suggested by
[http://ubuntuforums.org/showthread.php?t=291769](http://ubuntuforums.org/showthread.php?t=291769)

I'll keep updating

---

### Post by kebajonathan on 2006-11-25
**Solution:**

Add the following two lines into the "Device" section of your /etc/X11/xorg.conf:

```

Option "BusType" "PCI"
Option "DmaMode" "None"

```

---

