---
title: "Skype Installation"
date: 2005-09-12
forum: Installation &amp; Upgrades
---

### Post by hague56 on 2005-09-12
Dear Community,

today I installed skype on my 5.04 system as proposed on the official Wiki site. The installation finished fine, skype starts, displays all contacts but when I try to dial skype to skype or skype out, it is simply hanging in "connecting". The headset works fine (tested with the audio tools) and all the primary infos and changes did not show success. But the change of the esound parameters were impossible, as the system did not find it. What to do?

---

### Post by Leif on 2005-09-12
edit /etc/esound/esd.conf, change auto_spawn to 1. this solves the problem for me.

---

### Post by hague56 on 2005-09-13
[QUOTE=Leif]edit /etc/esound/esd.conf, change auto_spawn to 1. this solves the problem for me.[/QUOTE]

Thks Leif

I did it, but had to find out as well, that the libqt3c102 was not installed. After that skype works. Well, as I am using an old PII system slow and with a lot of echo and losses, but it works.

If you have as well some suggestions on the perfomance pbs, let me know. I am experiencing on UBUNTU, as I want to get rid of any windows based system...

Regs, Hague

---

### Post by Leif on 2005-09-13
you might want to use something other than gnome on an older system. try xfce or icewm.

sudo apt-get install xfce4
sudo apt-get install icewm menu

---

