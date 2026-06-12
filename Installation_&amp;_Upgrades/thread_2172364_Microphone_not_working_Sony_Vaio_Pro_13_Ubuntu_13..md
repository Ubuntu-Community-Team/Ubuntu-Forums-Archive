---
title: "Microphone not working Sony Vaio Pro 13 Ubuntu 13.10"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by asutton13 on 2013-09-04
Hey,
Have had great success so far running Ubuntu 13.10 on the Sony Vaio Pro 13 Haswell based laptop. Almost everything works great out of the box. The only component I've noticed an issue with thus far is the microphone. Currently on kernel 3.11rc7. Alsamixer, the system sound preference, and pavucontrol all show both a microphone (which I believe is input through the headphone jack) and an internal microphone. It's the internal mic I'm interested in using for quick skype calls or hangouts. Selecting the internal mic with pavucontrol and playing with the level settings in alsamixer hasn't made any difference. This issue has been noted running Arch linux as well, detailed [here.]("http://elouisyoung.blogspot.ca/2013/07/configuring-2013-sony-vaio-pro-13-with.html") Any ideas how to proceed? Perhaps this is a kernel related issue I should be reporting. Any help is greatly appreciated!

---

### Post by levince2 on 2013-09-07
Hi,
It may not help you but I got the exact same problem with Ubuntu 13.04.
a similar bug has been reported but is now expired:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1127699](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1127699)

---

### Post by asutton13 on 2013-09-09
Unfortunately this doesn't solve my issue. I have checked the mic levels under the capture section of alsamixer and i'm using the most up-to-date kernel I can find. Both the external and internal mic inputs are shown in alsamixer, pavucontrol, and sound preferences.

---

### Post by Toufik on 2013-09-12
Same issue with the same laptop, did you fill a bug report? You should!

---

### Post by Toufik on 2013-09-23
Bug report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1227093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1227093)

---

