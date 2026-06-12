---
title: "Nvidia + compiz = corruption"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eNry92 on 2009-02-27
i have this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904)

in jaunty

see the image and metacity:
[http://i40.tinypic.com/xp0tbc.png](http://i40.tinypic.com/xp0tbc.png)

here i report this bug:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/335405](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/335405)

---

### Post by taavikko on 2009-02-27
If you've founded existing bug. You don't start a new one, but give information to that existing bug.

Click "affects me too" or give additional information. And subscribe to that bug.

Starting new bugs on already existing bugs, creates bad signal/noise ratio. and creates extra work for bug triagers...

---

### Post by eNry92 on 2009-02-27
i alredy do this 5 month ago, but the problem ins't solved from intrepid to jauntu -.-

---

### Post by Nullack on 2009-02-27
Compiz breaks lots of things and wont be fixed until gpu memory management is properly implemented.

---

### Post by eNry92 on 2009-02-27
compiz 0.8 is out, but in repository there are 0.7.8 version
in final release we have compiz 0.7.8?

---

### Post by Vaun on 2009-02-27
You already pretty much Compiz 0.8 in the Jaunty repositories.  

0.7.9+git20090211-0ubuntu5 is a snapshot from 2/11/2009.  There haven't been many pushes since then.

You also have a recent snapshot of the plugins (main and extra).

---

### Post by eNry92 on 2009-03-01
i have install the update of today (nvidia driver 180.35)... no change... 
see the attachment

---

### Post by ZarathustraDK on 2009-03-26
I think I got this bug too, system freezes and borders start to get get messed up if I click arount with the mouse:

Asus M3N78 PRO motherboard
Nvidia 8300 onboard graphics
Athlon 64 X2 processor

It only occurs when compiz is enabled. Thought my mobo was bust (kinda mistreated it when mounting the cpu-cooler) so I bought a new one, no cigar, same problem.

Instances where I can reproduce it on a 100% basis :

- Wobbly windows seem to set it off after juggling the windows for a moment.
- Starting the "Open file"-dialog in Gnome from any program (like, choosing "File"->"Open..." in openoffice. Doesn't happen in XFCE.
- Starting Synaptic.

---

### Post by aethralis on 2009-03-26
I'm also affected, but not with NVIDIA but with Intel graphics (EG45M-DS2H Gigabyte card). See the attached screenshot (which is an old one from this bug report ([#335610]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/335610")), but the problem still persists).

---

