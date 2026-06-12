---
title: "sticking commands into modules file instead of modprobing"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by nzadLithium on 2008-01-03
hey i was using this:
```
modprobe --remove bt878 bttv
modprobe bttv radio=1 card=70 tuner=43 automute=0 audiomux=33,32,35,40 bttv_verbose=0 gbuffers=8 gpiomask=0x3F
modprobe btaudio
```
in my rc.local file to load my bttv stuff. Seems kind of stupid (it first loads bttv wrong then unloads then loads it right :D ) so i wanted to use the modules file to set up.

I put this in the file:

alias	char-major-81	bttv
options	bttv	radio=1	card=70	tuner=43	gpio_mask=0x3f	automute=0	audiomux=33,32,35,40	bttv_verbose=0

and now it doesnt load bttv right anymore :S what am i doing wrong? and can i get it to load btaudio from this file as well?

---

