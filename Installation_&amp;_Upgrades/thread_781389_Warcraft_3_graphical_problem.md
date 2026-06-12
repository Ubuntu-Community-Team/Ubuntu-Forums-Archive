---
title: "Warcraft 3 graphical problem"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by dr-phil on 2008-05-04
Hey guys,
I've only just recently installed ubuntu (removed the resource eating vista ultimate) and was quick to install my favourate game, warcraft 3 (i wanted to see how dota runs :) lol) Anyway, found out i had to install a window emulator etc. downloaded and installed both wine and playonlinux. Installed warcraft 3 + expansaion through playonlinux and tried to play except when i got into the home screen, it was all horrible, i got an error message but i couldnt read it because of the graphics. I dont think its a problem to do with my hardware considering it ran fine on windows vista.

when i ran wc3, my terminal:
Running Warcraft III : The Frozen Throne
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
preloader: Warning: failed to reserve range 00000000-60000000

Since i thought it was because of the graphics, i changed the 'directdrawrenderer' option in playonlinux from opengl to and gdi and vice versa but it made no difference.

Any help will be greatly appreciated;
Phil

---

### Post by mnk0 on 2008-05-30
what version of ubuntu are you using?? and version of wine and playonlinux. also what is the video card?

im using 8.04 with nvidia 8800gt and in wine works perfect, except there is a TABBING issue, and hosting. but apart from those, i can play perfect, and infact it runs better than it did on windows.


--
mnk0

---

### Post by dr-phil on 2008-05-30
Ah, dont worry, i got it working, turns out i had to chuck -opengl after the command line :) all fixed now. Thanks anyway

---

### Post by sorolop on 2008-06-23
Hello friends,its my second day using ubuntu :P

I install Wine(if there is something to see that it installed corect just tell me).
Then install Warcraft 3 & Frozen Throne(if there is something to see that it installed corect just tell me).

When i try to open it throught Wine the game graphics are REALLY BAD :(
I cant find my mouse anyware on wine's screen an if i click something there the application crash.
Then my hole pc screen has low detail graphics it seems to me it has litle brightness,and i must go to NVIDIA X SERVER SETTING and after clicking on that icon my graphics are fine.
Please someone help me!

---

### Post by bobe345 on 2009-07-19
wait i have this exact problem how did you get it working? what did you put intro the terminal.

---

