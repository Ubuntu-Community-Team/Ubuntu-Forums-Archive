---
title: "Duel-boot widows 7 &amp; Ubuntu 9.10"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by JohnL2009 on 2010-04-21
Here is the situation - I installed Windows 7 Ultimate, then Ubuntu 9.10. (mintlinux 64 kde)on a 2nd hard drive.  Ubuntu  booted up but no grub menu - so I reinstalled 7 - Now I can't get to Ubuntu.  I've read all the post, but nothing really makes sense.  Is there anyone who can post a simple easy to follow instruction to solve this problem?
Any help would be appreciated, thanks.

---

### Post by zvacet on 2010-04-21
You have to install grub on MBR so it can pick both OS.Reinstall grub following [this.]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

---

### Post by oldfred on 2010-04-21
Since you have 2 drives have you tried booting the other drive?

To see for sure where everything is installed at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by JohnL2009 on 2010-05-10
Follow up - thanks everyone, but I've tried everything and by looking at all the chatter about duel-booting windows 7 & ubuntu I've determined that neither pay nice with one another.  Windows 7 just doesn't like the competition.  Guess I will keep window 7 on one computer and Ubuntu on the other for now.

---

### Post by darkod on 2010-05-10
> **JohnL2009 said:**
> Follow up - thanks everyone, but I've tried everything and by looking at all the chatter about duel-booting windows 7 & ubuntu I've determined that [COLOR=Red]neither pay nice with one another[/COLOR].  Windows 7 just doesn't like the competition.  Guess I will keep window 7 on one computer and Ubuntu on the other for now.

Not to put any pressure on you, but that's simply not true. Yes, MS doesn't like competition and that's why they still don't make windows able to detect other OSs.

But I have Win7 Ult 64bit and Ubuntu 9.10 Desktop 64bit from the start (they got released approx at same time) and no issues at all.

Two days ago I installed 10.04 64bit over the 9.10 and no issues with 10.04 or win7.

Something else is bothering your system. If you feel like troubleshooting and learning, we're here. :)

---

### Post by JohnL2009 on 2010-05-11
Thanks for the reply - I'll give it a try again.

On 2nd thought - before I start again please tell me just how you did it.  Much apprediated.

windoow 7 partition is sda

Linux KDe partition is sdb

---

