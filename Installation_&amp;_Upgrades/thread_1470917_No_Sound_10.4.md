---
title: "No Sound 10.4"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by retro89 on 2010-05-03
I have no sound and I have installed gstreamer plugins and ubuntu restricted extras.

---

### Post by erdanblo on 2010-05-05
Me too. I did a fresh install.

I don't have sound with Ubuntu 10.4 LTS (32 bits / 64 bits).

I have Dell Optiplex MT380. Integrated Intel sound card.

**In Ubuntu 9.10 i had sound.**


**_lspci_**
[INDENT]_Ubuntu 9.10_: 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)[/INDENT]
[INDENT]_Ubuntu 10.4_: 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)[/INDENT]

At both version this is the which use (same output):
_cat /proc/asound/card0/codec#0 _
Codec: Realtek ALC269


I've installed **linux-backports-modules-alsa-2.6.32-21-generic-pae**, reboot system and nothing happens.



lsmod | grep snd

Ubuntu 9.10.
[INDENT]snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  4 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm[/INDENT]

Ubuntu 10.4
[INDENT]snd_hda_codec_realtek   208733  1 
snd_hda_intel          20384  4 
snd_hda_codec          79300  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5668  1 snd_hda_codec
snd_pcm_oss            34571  0 
snd_mixer_oss          13961  1 snd_pcm_oss
snd_pcm                71489  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1498  0 
snd_seq_oss            27658  0 
snd_seq_midi            4621  0 
snd_rawmidi            19141  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                48170  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18720  2 snd_pcm,snd_seq
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55971  21 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7236  2 snd_hda_intel,snd_pcm[/INDENT]

---

