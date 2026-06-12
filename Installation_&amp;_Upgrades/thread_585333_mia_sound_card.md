---
title: "mia sound card"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by winston84 on 2007-10-21
OK i just installed gusty and my sound card will not work. It shows up in a lsmod
but no sound now searches I've done say I have to compile alsa which give me even 
more errors. why should I have to compile this card (echo mia) has been around for 
years and has alsa support but never installs with any distro not every one uses 
on board sound if i have to compile it  its broken just give me a binary driver click and I'm done and don't ask me to make one I a musician not a programmer. [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)






snd_mia                31236  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_mia,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mia,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
snd                    54660  9 snd_mia,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

thanks Winston Smith

---

### Post by winston84 on 2007-10-21
well i downloaded the alsa source and compiled it and rebooted it works but the mixer is 
a bit buggy but it work not how to get my MOTU midi working fun fun .

---

