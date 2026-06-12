---
title: "Xubuntu in VirtualBox"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by jpatton on 2007-04-30
I can't find anything in the other forums related to this. I'm running Fiesty on an Acer Travelmate 250, Pentium 4 2.4Ghz, 512mb RAM, 100gb drive. I installed VirtualBox and was able to install a copy of Windows XP with no problems. I have been messing around with various Linux OS's, so I figured I should be able to install XUbuntu with no problems.

Well I can around with the virtual display being larger than my laptop's display, what I'm struggling with is it will go through the entire setup questionnaire process then it will lock up at the point at which the display says, Detecting Filesystem.

Any pointers would be greatly appreciated, I have yet to download the alternate .iso, which I'll do this evening, but I'm wondering if there is something else I can do in the meantime. I tried to wipe the virtual disk first, and have it build the partition structure. I've created a partition structure that it could use, I think it's just something silly I'm missing.

Thanks in advance!

---

### Post by Ziox on 2007-04-30
There seems to be some problem with Xubuntu Feisty.  I read on another thread where the system freeze at the exact place as yours.  What you can do is, install a command line system from the Ubuntu Disc, and then install the xubuntu package.

sudo apt-get xubuntu-desktop

Hopefully the problem gets fixed soon.

---

### Post by jpatton on 2007-04-30
Was the OP in the thread you were referring to attempting to install Xubuntu in VirtualBox?

---

### Post by jpatton on 2007-05-01
Xubuntu installed in VirtualBox using the alternate CD. Not sure why other than perhaps some incompatability between Xubuntu and its interaction with a virtual video card that causes it to lock up. 

But, installing Xubuntu using the text mode install on the Alternate CD worked like a charm.

---

