---
title: "no soundcard: remove ALSA lib * errors"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by not_a_commie on 2007-04-11
After updating to Edgy from Dapper I get the following message no matter what I run. It's a server board and always has been. I don't have a sound card. How do I disable this?

ALSA lib confmisc.c :670: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c :3479: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c :391: (snd_func_concat) error evaluating strings
ALSA lib conf.c :3479: (_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c :1070: (snd_func_refer) error evaluating name
ALSA lib conf.c: 3479: (_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c: 3947: (snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c: 2146: (snd_pcm_open_noupdate) Unknown PCM default

---

### Post by SPace_Pirate_Arrr on 2007-04-25
I have exactly the same problem, with exactly the same error messages.

I installed ubuntu on one box, then transferred the hard drive into another.  The new box is an old compaq and may well have an unsupported sound card.

Like the OP, I don't need sound.  I just want the error messages to go away.  

Can Anybody suggest a fix for this?

---

