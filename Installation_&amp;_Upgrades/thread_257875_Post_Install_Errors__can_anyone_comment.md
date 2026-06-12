---
title: "Post Install Errors:  can anyone comment"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by Nap_BlownApart on 2006-09-15
I've installed Ubuntu 6.06 Server, and decided to install Gnome with Nautilus.  The reason for the GUI is because I'm new to Linux and with the GUI I can immediatly start doing a lot of things.

Basically, everything is working fine.

I wanted to edit the /etc/apt/sources.list file, so I opened a termina window and typed:
```
sudo gedit /etc/apt/sources.list
```
I was asked for a password, which I provided.
Edited the file, and saved it.
When the editor closed, I saw these errors reported in the terminal window.  Can anyone comment on what they mean?

```
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

```

Cheers,
Nap

---

