---
title: "No sound with CD-Player"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by RoboRob on 2005-03-30
HI,
I'm a total linux-n00b, and I'm trying to get my only soundcard, Terratec Aureon 7.1 - Universe, to work with ubuntu.
When looking at the Volume Control I see 2 tabs:
- ICE1724  - multitrack[OSS mixer]
- Terratec Aureon 7.1 - Universe[Alsa Mixer]
I have nothing muted on either tab. When I open CD-Player to play an auio-CD I get no music.
The only sounds I get are the system sounds like the clicks en opening sound when I log on.

---

### Post by scoon on 2005-03-30
Hey there, 

Open up a terminal and run alsamixer.  Mute/un-Mute and adjust volumes as necessary.  You can read about the alsamixer by typing man alsamixer in a terminal. 


scoon

---

### Post by RoboRob on 2005-03-30
Already opened the alsamixer in the console and played with it with no luck.

RoboRob

---

### Post by kagou on 2005-03-30
Just a n00b question :
Is there a cable between cd drive and sound card ?

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Terratec#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Terratec#matrix)

---

### Post by RoboRob on 2005-03-31
[QUOTE=kagou]Just a n00b question :
Is there a cable between cd drive and sound card ?

Good question, but Yes there is a cable connected from the CD-drive to the Soundcard.

---

