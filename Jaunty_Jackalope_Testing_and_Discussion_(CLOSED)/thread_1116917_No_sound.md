---
title: "No sound"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jjroper on 2009-04-05
When I installed Jaunty I lost my sound.

I reviewed the many messages (but, all in older versions of Ubuntu) about this, so:

I discovered my model - STAC9205

Modified my alsa-base.config to include it. Then, I went through the list of several other things to modify (won't include them all here, but including the default.pa file as well).

Nothing works.  No sound.

I have a Gateway laptop, M-series.

Any suggestions?

Jim

---

### Post by krausest on 2009-04-05
> **jjroper said:**
> When I installed Jaunty I lost my sound.

I reviewed the many messages (but, all in older versions of Ubuntu) about this, so:

I discovered my model - STAC9205

Modified my alsa-base.config to include it. Then, I went through the list of several other things to modify (won't include them all here, but including the default.pa file as well).

Nothing works.  No sound.

I have a Gateway laptop, M-series.

Any suggestions?

Jim

If you've verified with alsamixer -Dhw:0 that all channels are unmuted and have turned all volume bars up, then you might check whether you need to add an module "model" option in /etc/modprobe.d/options (Create it if it doesn't exist)
I have a STAC9271D in my notebook and since 2.6.28 I have to add the following option in /etc/modprobe.d/options:
options snd-hda-intel model=5stack index=0
A list of all models can be found on: 
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

---

