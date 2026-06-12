---
title: "ALSA errors after updating to 7.04"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by HappyDude on 2007-06-19
Many applications that I use seem to output tons of ALSA error messages, indicating that there is no 'default' device, now that I've upgraded to 7.04.

Running "alsamixer" from the command line gives the error "alsamixer: function snd_ctl_open failed for default: No such device";  however, running "alsamixer -c0" successfully opens the mixer for my one and only soundcard.

The Ubuntu system sound check thing doesn't work if anything is set to ALSA.

Can anyone help?

---

