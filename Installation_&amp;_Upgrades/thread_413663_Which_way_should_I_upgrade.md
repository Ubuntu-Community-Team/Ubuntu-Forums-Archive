---
title: "Which way should I upgrade?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Databit on 2007-04-19
I originally installed Ubuntu then I installed KDE via synaptic. Now it says Kubuntu. So do I run the upgrade for Kubuntu to Ubuntu?

---

### Post by residualbit on 2007-04-19
it depends on which desktop interface you would rather run...KDE (kubuntu) or GNOME (ubuntu)...personally i like gnome better but its really whatever you are more comfortable with

---

### Post by Podex on 2007-04-19
You can have both Kubuntu and Ubuntu. In the login screen you can chose your Desktop environment. You probably still have Gnome, the official Desktop environment for Ubuntu.

---

### Post by Databit on 2007-04-19
Ah so the K does just mean "has KDE" I didn't know if it had any other features associated with it that might cause issues later.
I'm basically getting back into Linux. I've been loving Windows since Win2k but Vista is just plain gross. Pre win2k I was into Linux a good deal. So now I'm trying to figure out which interface I like and I'm switching between Gnome and KDE once every few days. 

So should I install the upgrade on both? Login to a KDE session. Run upgrade. Login to Gnome session and run upgrade or will one pretty much cover it?

---

### Post by Podex on 2007-04-19
If you already have both it should upgrade all the packages from both DE's. As far as I know anyway ;)

---

### Post by PriceChild on 2007-04-19
just run:
```
sudo apt-get install ubuntu-desktop kubuntu-desktop
```then run the standard distribution upgrade procedure to feisty.

---

### Post by xadder on 2007-04-19
You should probably use aptitude, not apt-get, for installing (k)ubuntu-desktop. See:

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Seems to keep life a bit simpler.

---

