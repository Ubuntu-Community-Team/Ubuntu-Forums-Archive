---
title: "drm kms helper panic during upgrade to 14.04"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by be4truth on 2014-04-18
I am upgrading from 13.10 to 14.04 64 bit. Started the upgrade software. Downloaded all required packages and then came with an error message that the Xscreensaver and Xlock had to be restarted. After proceeding I got a black screen and a drm kms helper panic ( see attachment)

Laptop boots fine but can't continue with upgrade. Any idea what to do now? There are Inter graphic chips on board. Laptop is a Linux tested laptop. Had never any problems with any hardware.
I pressed the power off button after the freeze. Laptop boots fine and is function. After trying to apt-get distupgrade I get a message to run dpkg --configure -a first which leads again to the above error.
[ATTACH=CONFIG]252191[/ATTACH]

---

### Post by be4truth on 2014-04-19
Got this problem fixed by booting into recovery mode (press shift key while booting) and went to the dpkg repair option. The installation routine continued and got stuck once more and I repeated this until it eventually installed all. Computer booted fine into 14.04.

---

