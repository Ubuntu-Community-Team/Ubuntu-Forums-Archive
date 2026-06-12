---
title: "How can i get my soundcard working?"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by ruvil on 2005-08-11
Yes.. how can i get my Soundblaster live! 24-bit working?
Iam using ubuntu 5.04 and the version of alsa that comes with it. (Think its 1.0.8 os something like that)
Is there any way to install alsa from the breezy badger? Cuz i think that version is newer, and where can i grab it.. and so on?

---

### Post by BanskuZ on 2005-08-11
```
sudo cp /etc/modules /etc/modules.bak
sudo gedit /etc/modules
```
Add:
```
snd-pcm-oss
snd-ca0106
snd-mixer-oss

```

---

### Post by ruvil on 2005-08-11
no.. i couldnt get that working :S
i added that lines, rebooted and.. it still says "no sound device" (or thins like that)
i tried to play an audio file in some diffrent programs like xmms, mplayer, totem :/

You maybe know why? or can i do something else to get everything working?

---

