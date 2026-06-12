---
title: "audio problems with headphone jack 9.04"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bootninja on 2009-04-07
Ok, so I've already spent several hours pouring over related threads, and I've tried several of the fixes, with no results.

I've got the Gateway M-6864FX laptop running Jaunty.  when I use the built in speakers, I get sound just fine, but when I plug in my external speakers through the headphone jack, suddenly I have no sound.

output from cat /proc/asound/card0/codec#* | grep Codec

gives me


Codec: SigmaTel STAC9205
Codec: Conexant ID 2c06

I've tried adjusting my alsa-base.conf, adding the line

options snd-hda-intel model=auto

I've tried model=3stack, 6stack, dell-m42, dell-m43, and dell-m44, but to no avail.

all my sliders are NOT muted, and when I go to switches in volume control, there is no switch for headphones.  I think that's probably telling, but I don't know what to do about it.

any suggestions you guys have would be very helpful.

---

