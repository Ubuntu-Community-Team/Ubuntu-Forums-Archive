---
title: "Speakers not working"
date: 2008-08-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wbutchart on 2008-08-07
HI i have installed Alpha 3 on my laptop (not as main system).  I have noticed that everything is working other than the sound.  When i am at the log in screen i hear the drum roll but once logged in no sound at all.  I have tried mp3 files and stuff but whilst they play there is no sound.

I checked the volume settings and they all seem fine.

Sound works fine on 8.04

---

### Post by loboc on 2008-08-07
It may be depending on pulseaudio but pulse might night be starting, try changing your output to alsa in Preferences>Sound 

Or run ```
pulseaudio&
``` in a terminal

---

### Post by wbutchart on 2008-08-07
Hi when i ran that code in the terminal i got the following back - 

W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
[1] 5366
[1]+  Exit 1                  pulseaudio

---

### Post by philinux on 2008-08-07
Pulse audio is bugged. The sound is actually coming out the pc speaker.

Change to alsa for now till it gets fixed.

---

