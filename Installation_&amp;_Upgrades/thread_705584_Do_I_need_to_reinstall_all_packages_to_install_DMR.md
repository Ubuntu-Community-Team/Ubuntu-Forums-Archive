---
title: "Do I need to reinstall all packages to install DMRAID?"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by richterlevania3 on 2008-02-23
Hi, I´m a new user of Ubuntu and my wish is to get rid of Window$ as fast as possible. Well, I´m trying to install Feisty on a Nvidia Raid 0 system. I was following the instructions of a tutorial I found here, but when I try to install Dmraid it asks to install other package first, a dependency (I forgot its name). Well, I downloaded that package and tried to install it, and it asks for a dependency, libc6. But libc6 is already on the system! 

So, how do I do to install Dmraid and Bootstrap without being connected to internet? Do I need to reinstall packages that are already in the Live-CD?

Thx in advance.

---

### Post by Partyboi2 on 2008-02-23
you could use something like [nonetdebs]("http://nonetdebs.homeip.net/") to install packages without having a woking internet connection with ubuntu.

---

### Post by richterlevania3 on 2008-02-24
Thx for answering, but you didn´t answer one thing that is annoying me: when I try to install libc6 Ubuntu says it is already installed, but when I try to install libdevmap (I don´t remember if this is its correct name) it says it needs libc6 as a dependency. So, this is an unending circle, one saying it is installed and other saying it isn´t.

The whole scena is this: I´m trying to install Ubuntu Feisty on a NVRaid 0 (nVidia) that already has a Windows installed (Yes, I know, but when I get success installing and playing WoW smoothly the first thing I will do is get rid of Window$). It´s splited in two partitions, the first one with Window$. These are the system specs:

Atlhon 64 4200+
2Gb Corsair DDR400
ASUS A8N-SLI Premiun
gForce 6800 Ultra
2x 40Gb Maxtors in Raid 0

I hope you can help me installing it without net, even if I would need to redo all the system.

Thx in advance.

PS: nonetdebs are offline ATM.

---

### Post by Partyboi2 on 2008-02-24
When you downloaded the dmraid package did you download the version for feisty or gusty? If you you downloaded the one for gusty this will cause a libc6 dependency problem. [Here is the feisty package ]("http://packages.ubuntu.com/feisty/dmraid")if you have accidentally been trying to install the gusty one. :)

---

### Post by richterlevania3 on 2008-02-26
Many thanks to you, pal. I haven´t tested it yet, ´cause I´m at school now, but this MUST be the problem! Oh, God, help me get rid of Worsedow$ today!
I will update this thread to [Solved] if everything goes fine.

Thx again.

---

