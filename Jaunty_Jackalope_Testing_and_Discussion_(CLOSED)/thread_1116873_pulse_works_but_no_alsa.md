---
title: "pulse works but no alsa?"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by snkiz on 2009-04-05
Wtf? when is this going to work this time around pulse seems to be working fine but not alsa. heres what I've got:```
00:0a.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
	Subsystem: Ensoniq Device 2003
	Flags: bus master, slow devsel, latency 32, IRQ 12
	I/O ports at b000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ENS1371

```
```
~$ aplay -l
aplay: device_list:217: no soundcards found...

```
```
~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
```
```
snd_ens1371            30496  3 
gameport               19340  1 snd_ens1371
snd_ac97_codec        112292  1 snd_ens1371
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82820  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  16 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```

```
~$ lsof /dev/snd/*
COMMAND    PID    USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 3527 ckadmin   22u   CHR  116,8      5763 /dev/snd/controlC0

``` and I have a login sound. so very lost here

---

