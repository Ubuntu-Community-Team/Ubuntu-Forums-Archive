---
title: "Installed Gstreamer-Mad -&gt; Total Crash"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by floe-de on 2005-07-10
Hallo,

I have installed Ubuntu 5.04 on my IBM Thinkpad T43 Laptop with no problems, 
but then I installed gstreamer-0.8-mad to hear MP3s.
The Installation said no error so I click on an MP3, Totem started an then
my Laptop totally freezed. I can't do anything, not changeing the console or reboot,
so I must shutdwon the computer by pressing the power button.

After restarting I testet Rhythmbox the same effect.

I installed Ubuntu new and test a OGG File -> no problem I can hear the music
so I think a was an install error I installed gstreamer-mad the second time and
my computer freezed. I power down restart and deinstalled the gstreamer-plugin
but now the error is allway there even when I want to play the OGG file.

So what can I do to beware my pc from freezing ?

---

### Post by adwait on 2005-07-10
Umm, you could try changing the output plugin used by gstreamer. To do this, type gstreamer-properties at the teminal. Try using ALSA, OSS, ESD...one of them's gotta work.

---

### Post by floe-de on 2005-07-11
It worked after changing Multimeda System Control Input from OSS to ESD.
Thanks a lot...

---

