---
title: "dead black screen instead of log-in"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by blastradius on 2006-11-30
Hi all!

I've tried installing Edgy and Dapper including the alternate version of Dapper, and I still get the same problem.  The system installs fine, it boots fine but then just as I expect the login screen to appear it stays as a dead black screen!  The boot-up screen is fine so where is my log-in screen.

At this rate I'll have to re-install Hoary and try to upgrade from there.  What the hell is going on?

My GFX card is an ATI Radeon 9600 and the monitor is a standard Relisys.  I had no problems with Hoary so how come I've got them now?

Please help!

Eric

P.S. I'm having to type this on Windows!!!  HELP!

---

### Post by an.echte.trilingue on 2006-11-30
You need boot into recovery mode, edit your sources.list to include universe and multiverse, sudo apt-get fglrx, and then sudo dpkg-reconfigure xserver-xorg.

Edit:  Made a typo

---

### Post by blastradius on 2006-11-30
Ok, one question.  Which editor do I use, I've always used Gedit before but it doesn't seem to recognise it, I tried:-

sudo gedit /etc/apt/sources.list

---

### Post by That_Geek on 2006-11-30
sudo nano /etc/X11/xorg.conf
use nano, not gedit

---

