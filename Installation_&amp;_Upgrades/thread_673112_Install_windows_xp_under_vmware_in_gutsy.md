---
title: "Install windows xp under vmware in gutsy"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by ZeldaFan on 2008-01-20
If I wanted to install windows XP media center edition in ubuntu gutsy virtually, do I need to use vmware player or vmware server. I'm rather inexperienced in these kind of programs, so I'm pretty confused as to what I should get. And does anyone have a link to a guide that I should use to installing it? I found some online, but I wasn't sure which one is the best to use, so if someone has some prior experience with one already, it might be best if I use whatever you used. 
Also, I don't have a pure Windows XP install disk. My laptop came with windows xp MCE pre installed and came with like a recovery disk sort of thing (I have an HP dv9000t). It installs the factory settings, so in addition to Windows XP, it includes all the drivers, settings, and extra programs that came with my laptop. Would that kind of install disk work?

---

### Post by sowelie on 2008-01-20
I would recommend VirtualBox over VMWare.  You can install it through apt:
```
sudo aptitude install virtualbox
```

Also, that kind of disc most likely will not work.  It does not contain an actual installer for windows, it just has a hard disk image on it.  You will need an actual windows xp install disc.

---

### Post by ZeldaFan on 2008-01-20
Thanks for the reply, I will check out virtualbox. Well if that kind of installer does not work, I do have an actual windows XP install disk that is licensed to another Dell laptop I own. The XP disk is legal but because it is licensed to my dell, is it still legal to install it virtually on my HP computer, even though it isn't licensed to my HP? What about if I uninstall XP on my Dell and just use it on my HP? I don't want to have to buy a completely new operating disk to use XP virtually.

---

### Post by charlescarroll1 on 2008-03-04
> **sowelie said:**
> I would recommend VirtualBox over VMWare.  You can install it through apt:
```
sudo aptitude install virtualbox
```

Also, that kind of disc most likely will not work.  It does not contain an actual installer for windows, it just has a hard disk image on it.  You will need an actual windows xp install disc.

Where am I supposed to find this program after it has been installed?

---

### Post by kprateek88 on 2008-03-05
> **charlescarroll1 said:**
> Where am I supposed to find this program after it has been installed?
If you couldn't find it in the Applications menu, you can run 'virtualbox' from the terminal. You can add it to your Applications menu, though I don't know how this is done in Gnome.

---

