---
title: "amaroK and sound errors"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by OmegaOne on 2005-11-30
when i try and run any files in amaroK i get an error:
[GStreamer Error] ** gstmad.c(1206): gst_mad_check_caps_reset: /thread/decodebin7/mad8: Failed to negociate 44100 Hz, 2 channels

when i change the engine to osssink instead of aslasink it works ok. is this bad, and will it effect other applications? how can i make osssink my default (or check if it is)?

thanks

---

### Post by daller on 2005-12-01
It does not affect other applications...

You should consider installing "amarok-xine", and use that engine instead...

---

### Post by OmegaOne on 2005-12-04
[QUOTE=daller]It does not affect other applications...

You should consider installing "amarok-xine", and use that engine instead...[/QUOTE]

sorry im so late with this reply.

are you asking or telling me that it wont effect other applications?

thanks

edit: just changed to xine, and it runs faster and the sound quality is better :D. nice call, thanks!

---

### Post by daller on 2005-12-05
Nice that you got it solved!

In general, a package called "<APPLICATION>-xine" will only affect <APPLICATION>

---

