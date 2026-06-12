---
title: "audio not playing in 13.04 as i try ed commands"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by bhanuteja2 on 2013-08-13
sudo apt-get remove --purge alsa-base pulseaudio

sudo apt-get install alsa-base pulseaudio

sudo alsa force-reload

still not working

---

### Post by MG&amp;TL on 2013-08-13
What sound hardware do you have? You can find out with the manual that came with your machine, or you can paste the results of

```
lspci
```

in *CODE* tags, so that we can find out for you.

---

