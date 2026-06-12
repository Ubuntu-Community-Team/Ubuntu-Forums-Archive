---
title: "SB Live! not working in Jaunty"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by wolfshark on 2009-03-25
Hi, i have a strange problem. My soundcard was working perfectly under Kubuntu Jaunty, but today i installed Ubuntu Jaunty and and there is no sound. I looked into the Volume Control app and there is only Master and nothing else. On Kubuntu there were over 20+ controls here!
[[IMG]http://img407.imageshack.us/img407/7906/soundproblem.jpg[/IMG]](http://img407.imageshack.us/my.php?image=soundproblem.jpg)
Here is my lsmod output
```
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
snd_emu10k1_synth      14336  0 
snd_emux_synth         40704  1 snd_emu10k1_synth
snd_seq_virmidi        13440  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           144800  4 snd_emu10k1_synth
snd_ac97_codec        112292  1 snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82820  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16904  2 snd_emu10k1,snd_pcm
snd_util_mem           12288  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15108  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
nvidia               7239420  36 
snd_seq_midi_event     15104  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                56880  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
agpgart                42696  1 nvidia
snd_timer              29704  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14988  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                 12416  0 
emu10k1_gp             10752  0 
snd                    62628  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
ppdev                  15492  0 
gameport               19340  2 emu10k1_gp
soundcore              15200  1 snd
serio_raw              13316  0 
i2c_nforce2            14980  0 
pcspkr                 10496  0 
usblp                  20224  0 
usbhid                 42336  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
r8169                  40836  0 
mii                    13312  1 r8169
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```
It seems fine to me, my audio processor really is emu10k1
I am really struggling here, please help.

---

### Post by wolfshark on 2009-03-25
Problem Fixed

---

