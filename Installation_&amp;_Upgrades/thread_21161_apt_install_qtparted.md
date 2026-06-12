---
title: "apt install qtparted"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by jeffus on 2005-03-20
I would like to install qtparted, so in /etc/apt/sources.list I added the universe lists.  Then found qtparted w/ Synaptic and it said this:

> qtparted:
 Depends: libparted1.6-0 (>=1.6.0) but it is not installable

So I went to libparted and found libparted1.6-12, which was already installed.

I'm at a loss.  Any suggestions,

Jeff.

---

### Post by Gary Powers on 2005-03-20
Same problem.  In fact, I don't remember ever getting a proper install of Qparted although I have gotten it to work.  Which is why I keep a Windows installation (with Partition Magic) on each of my boxes.  There is a place for Windows, if only to help me learn Linux.

Gary

---

### Post by Mgcross on 2005-03-21
Simple fix:
sudo apt-get install gparted 
(same as qtpartd for gnome)

I had the same problem and GParted works just dandy!

---

### Post by Gary Powers on 2005-03-21
Thank you Mgcross, I will try that!

Edit:  worked like a charm.  Thanks.

Gary

---

### Post by Mgcross on 2005-03-21
No Problem- now could someone give me a hand getting TV-Out working? :-)

see post [http://www.ubuntuforums.org/showthread.php?t=21279](http://www.ubuntuforums.org/showthread.php?t=21279)

I've tried editing by hand, but no matter what I've tried I can't get X to restart when I hand edit the file.
I've tried nvtv and it segfaults
I've Tried YAnc but it gives me a QT error and then dies....

My wife is making Windows noises <shudder>

---

