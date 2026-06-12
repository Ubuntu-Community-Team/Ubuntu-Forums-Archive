---
title: "No sound after update xubuntu 8.10"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by oc666 on 2008-10-14
Hello
I update my system and now there is no sound.
My audio is:
> lspci | grep udio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
The modules that upload:
>  lsmod | grep hda
snd_hda_intel         381488  2 
snd_pcm                83204  3 snd_bt_sco,snd_hda_intel,snd_pcm_oss
snd                    63268  15 snd_bt_sco,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16136  3 snd_bt_sco,snd_hda_intel,snd_pcm

Thanks for the help.

---

### Post by overdrank on 2008-10-14
Moved to  Intrepid Ibex Testing and Discussion :)

---

### Post by Sam Lars on 2008-10-15
I had this problem too... except I upgraded Ubuntu and then added Xfce to it, which is almost the same thing.
I changed the setting in Settings > Multimedia Systems Selector to ALSA instead of PulseAudio.  That got the Test button working for me instead of putting up an error.
Do you get any errors?
Also, what programs have you tried for sound?  Rhythmbox still won't work for me, but I think it was Gnome Mplayer that ended up working.  Do Totem or other programs play any sound?

I have a
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

There are some bugs in Launchpad about your card... I'm not sure what their statuses are.

---

### Post by zeusfaber on 2008-10-16
i am running xubuntu ibex beta as well and have a 82801H sound card. after installing ibex from scratch my sound does not work any longer. prior to the install i did an upgrade from hardy to ibex and audio worked properly afterwards. anyone have any clues?

---

### Post by Sam Lars on 2008-10-17
I would try out some guide like [this]("http://ubuntuforums.org/showthread.php?t=866965").

---

