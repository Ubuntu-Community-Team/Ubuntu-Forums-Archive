---
title: "No sound at all for 2 weeks now"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by marttali on 2008-10-13
Hi,

i hope someone can help me out. After upgrade from 64 bit Kubuntu 8.04 to 8.10 i lost sound altogether. Here's a screen shot from my sound manager.
[screenshot]("http://i35.tinypic.com/dot09f.png")

I have installed all alsa, oss, pulseaudio libaries packages several times, my account has userrights to use audio and pulse*.
Few outputs from console:
```
mart@Kubuntu:~$ aplay -l
aplay: device_list:215: no soundcards found...
mart@Kubuntu:~$

```

```
mart@Kubuntu:~$ lspci -v | grep snd
        Kernel modules: snd-hda-intel
mart@Kubuntu:~$ lsmod | grep snd
snd_hda_intel         489264  0
snd_pcm_oss            52608  0
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0
snd_seq_oss            42368  0
snd_seq_midi           15872  0
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm

```
```
mart@Kubuntu:~$ lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Giga-byte Technology Device a022                
        Flags: slow devsel, IRQ 16                                 
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]   
        Capabilities: <access denied>                              
        Kernel modules: snd-hda-intel  
```

if i type in alsamixer i get "alsamixer: function snd_ctl_open failed for default: No such file or directory"

Please advise how to fix this..

---

### Post by syko21 on 2008-10-13
Use the livecd to test the sound and to make sure its not a hardware issue.

---

### Post by marttali on 2008-10-14
I seriously doubt it's hw issue, i lost sound with the upgrade from 8.04.
any other ideas what to check ?

---

### Post by philinux on 2008-10-14
If sound works from the livecd then reinstall.

---

### Post by Sef on 2008-10-14
> If sound works from the livecd then reinstall.

+1.  Sometimes, a clean install is the easiest and quickest way to fix an upgrade problem.

---

