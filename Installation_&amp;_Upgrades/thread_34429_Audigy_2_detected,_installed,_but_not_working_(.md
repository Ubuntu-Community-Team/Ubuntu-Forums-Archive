---
title: "Audigy 2 detected, installed, but not working :("
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by JorisK on 2005-05-14
Argh man, i'm struggeling already for hours with this problem. The previous version of ubuntu had no single problem with my soundcard but this version...

I reinstalled ALSA, reconfigured it... the system says things are fine but still no noise coming out of my speakers... I also can't enable the 'digital analog output jack'  in alsamixer...

I guess i'll have to wait until the next version of ubuntu appears :(

---

### Post by monchichi on 2005-05-14
go into a terminal and run the following (and copy & paste the output back here):```
killall esd;aplay -v /usr/share/sounds/pop.wav
```Make sure your user has permission to use the /dev/snd/* devices.
Make sure the speakers are plugged in! :) (Occams's Razor and all).

---

### Post by JorisK on 2005-05-15
[QUOTE=monchichi]go into a terminal and run the following (and copy & paste the output back here):```
killall esd;aplay -v /usr/share/sounds/pop.wav
```Make sure your user has permission to use the /dev/snd/* devices.
Make sure the speakers are plugged in! :) (Occams's Razor and all).[/QUOTE]

Nothing happens, just no sound :(

Edit: Anyone here who knows HOW TO toggle the 'digital / analog sound output' setting in alsamixer?? It's turned off but what do i need to do to get it on?

---

