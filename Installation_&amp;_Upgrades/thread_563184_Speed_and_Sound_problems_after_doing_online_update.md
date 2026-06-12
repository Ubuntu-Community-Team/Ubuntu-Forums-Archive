---
title: "Speed and Sound problems after doing online updates"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by DBMandrake on 2007-09-29
Hi,

Installed Fiesty Faun 7.04 on a Pentium 4 2.4Ghz, with Nvidia FX5900XT, Audigy 2 ZS, 1GB ram.

After installing everything was working great - video, sound, without any fiddling around, and performance was extremely snappy.

Then I let the automatic updates do its thing and download 120 updates - disaster!

Sound no longer works through esd, so no system sounds will play, and there is a very long delay launching any programs - typically a 10 second delay to open any control panel or application, compared to almost instantaneous launching before. :(

Another problem is some of the updates failed to install correctly (apt-get errors) which left dependency errors for openoffice which was prevening me from installing any packages until I removed open office.

Any ideas ? After such a promising start its disapointing that the automatic updates have rendered the system fairly unusuable. (Very slow and no sound)

---

### Post by Pumalite on 2007-09-29
Re-install. Turn off automatic updates. Be very careful and selective in the future. I don't update anything if I have a working system. At the next release, I do a clean install.

---

### Post by DBMandrake on 2007-09-29
I've reinstalled it from scratch and sound works fine and performance is good again.... :)

I'm not happy about leaving so many security related updates undone though - so I'll try and isolate which package it is. My guess is it is the updated kernel...

---

### Post by Pumalite on 2007-09-29
I bet on that too.

---

