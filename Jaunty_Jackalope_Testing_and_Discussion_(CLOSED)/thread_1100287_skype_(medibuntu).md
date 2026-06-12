---
title: "skype (medibuntu)"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by giorsat on 2009-03-19
this is the crash I get when I log in
/usr/bin/skype.real: relocation error: /usr/bin/skype.real: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference

any idea of what it means?

---

### Post by taavikko on 2009-03-19
Is the problem isolated to skype, or is anything else affected?

To test sounds, use something like
```
aplay /usr/share/sounds/question.wav
```
Did you hear the drums?

Skype may need to be configured by you to use correct audiomodule
Or pulse may need to be configured to allow alsa...

---

### Post by giorsat on 2009-03-31
only skype is affected. I think the problem is that sound is completely broken in jaunty for ich9 chipset so I'm using pulseaudio in ppa (it has a 15 instead of 14) . when skype starts it complains it cant' use 32bit libraries with this pulseaudio and then crashes.

---

