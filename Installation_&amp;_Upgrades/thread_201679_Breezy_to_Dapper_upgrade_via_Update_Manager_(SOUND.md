---
title: "Breezy to Dapper upgrade via Update Manager (SOUND problem, partitially solved)"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by gray380 on 2006-06-22
Hi All,

In the begining.
After installation of Breezy 5.10 I have once started alsamixer, have made corresponding adjustments (mute/unmute some channels) and a sound function normally.

Before upgrading to Dapper 6.06 the content of /etc/modules was:
```
lp
mousedev
psmouse
sbp2
sr_mod
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq

```

After updating (/etc/modules):
```

lp
mousedev
psmouse
sbp2
sr_mod
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq
piix
ide-core
ide-cd
ide-disk
ide-generic

```

The result of lsmod:

```
$ lsmod |grep snd
snd_mixer_oss          19296  0
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
snd_seq_midi            9088  0
snd_rawmidi            24704  1 snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24164  1 snd_seq
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54884  6 snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9600  1 snd

```

The system did not make any sound.

I have made following changes to /etc/modules:
```
lp
mousedev
psmouse
sbp2
sr_mod
snd-intel8x0
usb_storage

```
(I shall tell about last line in my following message.)

The result of lsmod:
```
$ lsmod |grep snd
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
snd_seq_midi            9088  0
snd_rawmidi            24704  1 snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_intel8x0           33248  4
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  3 snd_seq,snd_pcm
snd                    54884  17 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm

```

I have started alsamixer, have made corresponding adjustments and there was a sound. Kind of magic, is it? ;)

But now I should start each time after reboot "alsamixer" and make corresponding adjustments.

**The question is what I should to do for avoiding manual interrupting with sound configuration?**

brg,
Serhiy.

---

### Post by gray380 on 2006-06-22
The problem was solved after installation of the correct version of a kernel. 
Why it was not updated by the Updte-manager while upgrading? (rhetorical question)

---

