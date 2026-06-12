---
title: "sound problem with dell inspiron 600m and SIGMATEL STAC 9750 AC97"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by morguns on 2006-03-04
i'm fairly new to ubuntu and linux, and i'm having problems getting sound to work. for some context, i originally installed hoary a few months ago and used it a little bit off and on. now i'm to the point that i want to switch to linux exclusively (long live tux!) i never got sound working in hoary and didn't stress on it too much, but now that i'm going "all the way", sound is much more of an issue.

i successfully upgraded my hoary install to breezy (after repairing the grub bootloader because i had to reinstall windows because windows disappointed me for (hopefully) the last time), but it wasn't what i'd call a painless process. my wireless configuration was about the only thing to survive the transition lol. eg. x-windows and my video drivers died horribly. but with a little patience and leg work i got them both up and running again. i can't guarantee they're running "right", but they're working and that's what counts :)

i've searched these forums and google high and low but have been unsuccessful in finding a solution to the sound problem. several times i found threads/pages with references to alsa, alsamixer, modprobe, etc but they didn't give me that needed push in the right direction. with that said, can someone(s) help me out?

here's some info that, according to other threads, should be helpful in resolving my issue. i don't know what to make of it personally, so some guidance would be much appreciated.

thanks in advance...

$ sudo lspci -v | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

$ lsmod | grep snd
snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

---

### Post by the.allstar on 2006-10-10
Anyone have a solution for this problem? I am experiencing the same on my Dell Inspiron 5150.

---

