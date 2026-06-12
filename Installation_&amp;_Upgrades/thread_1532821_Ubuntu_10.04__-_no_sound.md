---
title: "Ubuntu 10.04  - no sound"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by ahalin on 2010-07-17
This is the simplest solution I have ever found, having struggled through the loss of sound problem EVERY time I install a new Ubuntu distro or do an upgrade. (One has to wonder why this is the case.)

press Alt-F2 and type:

[INDENT]gksudo nautilus[/INDENT]

When Nautilus opens, navigate to and open the file /etc/modprobe.d/alsa-base.conf then add:

[INDENT]#this is the simplest post upgrade/installation fix for no sound in Ubuntu that I have seen:
options snd-hda-intel model=ref[/INDENT]

save and close and you should be in business. It worked with an HP and a Dell.

Taken from LazerPhreak's post at:

[http://www.linuxquestions.org/questions/linux-hardware-18/no-sound-ubuntu-10-04-hp-mini-110-a-798751/](http://www.linuxquestions.org/questions/linux-hardware-18/no-sound-ubuntu-10-04-hp-mini-110-a-798751/)

---

