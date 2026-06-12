---
title: "No alsa sound on ASUS M4N78 Pro Motherboard with Lucid"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by skipperx on 2010-06-02
I just did a clean install of 32 bit-Lucid on a DIY box with this mother board and AMD AthlonII X4 CPU. The MB has an NVIDIA IGP GeForce 8300. I have installed the current Nvidia driver and removed the pulseaudio. The system is up-to-date with apt-get update. I have tried playing videos and mp3 files and there is no sound.I would appreciate if someone can help me get the alsa sound working. I am posting what I thought was the relevant information for the experts to figure out:

Yes, I have unmuted and maxed out the volumes in the alsamixer.

```
$ modinfo soundcore
filename:       /lib/modules/2.6.32-22-generic-pae/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     51925557ECF0F2838930862
depends:        
vermagic:       2.6.32-22-generic-pae SMP mod_unload modversions 586TSC 
parm:           preclaim_oss:int

```

```
$ lsmod |grep snd
snd_hda_codec_via      27111  1 
snd_hda_intel          22005  0 
snd_hda_codec          74201  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  11 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm

```

```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

```

```
$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfad78000 irq 21

```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, VT1708S Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Digital
    IEC958 (S/PDIF) Digital Audio Output
```

Please let me know if I need to post other stuff.

Thank you.

---

### Post by dino99 on 2010-06-02
install paprefs and gnome-alsamixer and set your prefs with it (app sound gnome-alsamixer)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by skipperx on 2010-06-02
I installed gnome-alsamixer and checked the settings. Everything was already unmuted the master was max. I set everything max except mics.

I have not installed paprefs because it seems it is for the pulseaudio. When I read around, many people with alsa problems resolved their problems after removing pulseaudio. So, I removed pulseaudio. Not that I know much about either. I am just trying to make the sound work properly.

BTW,When I tried System>Perferences>Sound, I got only
"waiting for sound system to respond" msg on a small window and nothing else.

Do I need to add something at the bottom of alsa-base?
Do I need to add some settings in a file in /etc/modprobe.d/xxx?
How do I know if via chip or something setting is correct for the mobo in alsa?

I know this mobo is a challenging to get the sound right. Unfortunately this is what I've got. Can someone please help me.

---

### Post by skipperx on 2010-06-02
Well, using the alsa upgrade script from this form, I have installed the current alsa driver. It went successfully and I heard the drum beat for the first time at the first boot which was encouraging. However, it no sound and no more drum beat later. When I ran alsaconf, no card was found. But when I ran alsamixer, all speakers/ports were there. I unmuted and maxed out the volumes. Still no sound.

I think the solution is near, someone reading this please help me.

---

