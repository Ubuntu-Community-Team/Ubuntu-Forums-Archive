---
title: "First Time Installer- Few questions!!! Please Help."
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by nhjrmonarchs7 on 2008-02-18
Hey all,

I am about to make the switch from XP to ubuntu and will use beryl etc...few questions though.

First off my system specs:
Intel core 2 duo 6850
asus p5n-32e sli mobo (680i)
2 gigs of ballistix memory
2 74gb raptors raid 0 (windows and games)
2 100g maxtor drives in raid 0 (media)
nvidia 8800gt
coolermaster 1000w PSU

1)I am not dual-booting, however, do I need to do anything special to get ubuntu to see my media drives in raid 0? I do not want to format them or lose the data. Is it possible to just install ubuntu and it will pick up on the drives current setup?

2) Do i need to install specific raid drivers?

3) Any input that you can give...I appreciate. Again, I am going to format the raptors and put ubuntu on those, and keep my current media drives as they are. Is this possible?

---

### Post by Toet on 2008-02-18
Do you use your motherboard to do the raid, or do you have an separate raid controller to do this?

---

### Post by nhjrmonarchs7 on 2008-02-18
using the 680i onboard raid controller (NVraid).

---

### Post by Toet on 2008-02-18
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

This might be a good thing to read.

When I setup (software)raid myself I use mdadm, starting with an alternate install cd of Ubuntu. Google for it (mdadm, ubuntu) and you'll find good information.

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Is a nice link.

---

