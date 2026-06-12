---
title: "No sound 13.04 Asus eeebox 1501P"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by vedix on 2013-06-02
After upgrade to 13.04 sound disappeared in front output and rear headphone/spdif output. HDMI sound is working.
I have muted/unmuted checked volymes in alsamixer, and tried to change settings in pavucontrol, also tried reinstalling alsa and pulse.
I get the following message when i boot.

```
libkmod: Error ../libkmod/libkmod-config.c:686 kmod_config_parse:  /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with  ´snd-hda-intel´
```

Asus EEEbox 1501P

---

### Post by dralbin82 on 2014-01-02
I'm also having problem with spdif out on my 1501P in Ubuntu. I use 12.04 64 bit and all of sudden no sound on the spdif, probably after an upgrade. I have an old note of adding 
options snd-hda-intel model=6stack-dig
 to /etc/modprobe.d/alsa-base.conf but that does not help. 

I do not have the same error message as you.

Have you solved your problem?

---

### Post by dralbin82 on 2014-01-02
realized my optical cable was broken. a new one and it works again! :)

---

