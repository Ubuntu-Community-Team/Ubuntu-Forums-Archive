---
title: "no sound, I believe is ALSA related, Could not open /lib/modules/2.6.32-25-generic"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2010-09-10
```
hihihi100@hihihi100-laptop:~$ depmod -a
FATAL: Could not open /lib/modules/2.6.32-25-generic/modules.dep.temp for writing: Permission denied
hihihi100@hihihi100-laptop:~$ 

```another one I tried before this one:

```
hihihi100@hihihi100-laptop:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:654: audio open error: No such file or directory
hihihi100@hihihi100-laptop:~$
```also please check: [http://www.alsa-project.org/db/?f=6be1c3fdfea8d7d9891c933bbb6fd08cc2eaee7d](http://www.alsa-project.org/db/?f=6be1c3fdfea8d7d9891c933bbb6fd08cc2eaee7d)

which is the output for:

```
hihihi100@hihihi100-laptop:~$ wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh

```thx

---

