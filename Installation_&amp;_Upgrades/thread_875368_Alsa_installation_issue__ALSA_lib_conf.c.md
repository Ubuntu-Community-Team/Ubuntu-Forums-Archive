---
title: "Alsa installation issue:  ALSA lib conf.c"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by ash12345 on 2008-07-30
Hi All,
I installed ALSA on my ubuntu 7.04 and have issues with my audio.  Any command or process involving ALSA will give the following error:

ALSA lib conf.c:1177: (parse_def) dsnoop is not a compound
ALSA lib conf.c:1587: (snd_config_load1) _toplevel_:24:32:Invalid argument
ALSA lib conf.c:2848: (snd_config_hook_load) /root/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075: (snd_config_update_r) hooks failed, removing configuration


I am not able to use my inbuilt sound card's audio.  The inbuilt sound card is Cirrus Logic CS 4297A.  Through research I found out that ALSA doesn't support this particular sound card.  Is their any other way I can make this work?
Thanks,
Ash

---

### Post by ash12345 on 2008-07-31
The problem is resolved.  Their was a wrong configuration file that was causing this.  I removed the file and it works fine.

---

