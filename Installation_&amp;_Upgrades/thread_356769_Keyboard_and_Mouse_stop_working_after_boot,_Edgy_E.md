---
title: "Keyboard and Mouse stop working after boot, Edgy Eft"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by Threevolve on 2007-02-08
Weird problem, upon starting Live CD, the keyboard and mouse stop working. No idea why. Tried different keyboards and mice, some USB, some PS/2. None will work.

System is not hung, as when I push the power button, the shutdown dialog pops up.

No idea why this is happening, I've been using Ubuntu for a while and I have never seen anything like it.

Any ideas?

---

### Post by revoltism on 2007-02-13
try reconfigure xserver...

```
sudo dpkg-reconfigure xserver-xorg
```

follow the wizard it might fix the problem... or directly in /etc/X11/xorg.conf

---

### Post by flying_split on 2007-02-15
I have this same prblem with a family members computer I know its not the keyboard or the mouse causing the problem as they work find on my other computer that runs ubuntu . Im also using the same livecd so Im not sure whats going on . also cant enter any commands because the keyboard does not respond . 
Cant someone help. I have seen several topics on this with no answer. come on guys its a great system that I`m trying to convert the world too but with this sort of problem makes life difficult

---

### Post by chickensofdoom on 2007-02-15
I've found that hitting keys during boot makes the keyboard work. I can't get the mouse to work though =\

---

### Post by donatell0 on 2007-02-15
I desperately hope that hitting keys on the keyboard will make the keyboard work. I desperately want to install edgy on my home comp (that presently runs xp)... I've been using dapper on my hostel comp and really love it. I hope someone has a good fix for this problem!

---

