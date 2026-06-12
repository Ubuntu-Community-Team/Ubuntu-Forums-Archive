---
title: "MAJOR Sound problems with UBUNTU-One stereo channel does not function"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by mikewave on 2007-01-07
When using any audio or video application, sound ONLY comes from the left channel. I have checked all physical connections and all sound hardware (a SONY stereo receiver with two Minimus-7 loudspeakers). Everything is normal.

My sound card is an M-Audio Delta 410. I chose it because I understood it to be compatible with Linux.

With a previous installation of KUBUNTU linux, the sound card performed normally.

This computer is a dual-boot unit. That is, it uses one of two IDE hard drives, both of which are in removable plastic caddies, one containing Ubuntu Linux, the other containing Windows 98SE. IOW, when one HD is inserted, the box is a Linux box, when the other one is put in place, the box is a Windows 98SE box.

When the WIN98SE HD is put in place, the sound card performs normally.

The last time I installed updates to Ubuntu Linux was on 4-JAN-07.
](*,) 

Platform  	1 Ghz PIII, 256 MB of RAM, 80 GB HD
Ubuntu Linux (Gnome)(Dapper Drake?)
OS Version 	6.06 LTS

---

### Post by justifier on 2007-01-07
my advice would be to check all your sound drivers

---

### Post by justifier on 2007-01-07
also is it set to mono?

---

### Post by Lord Illidan on 2007-01-07
> **mikewave said:**
> When using any audio or video application, sound ONLY comes from the left channel. I have checked all physical connections and all sound hardware (a SONY stereo receiver with two Minimus-7 loudspeakers). Everything is normal.

My sound card is an M-Audio Delta 410. I chose it because I understood it to be compatible with Linux.

With a previous installation of KUBUNTU linux, the sound card performed normally.

This computer is a dual-boot unit. That is, it uses one of two IDE hard drives, both of which are in removable plastic caddies, one containing Ubuntu Linux, the other containing Windows 98SE. IOW, when one HD is inserted, the box is a Linux box, when the other one is put in place, the box is a Windows 98SE box.

When the WIN98SE HD is put in place, the sound card performs normally.

The last time I installed updates to Ubuntu Linux was on 4-JAN-07.
](*,) 

Platform      1 Ghz PIII, 256 MB of RAM, 80 GB HD
Ubuntu Linux (Gnome)(Dapper Drake?)
OS Version     6.06 LTS

Check your volume controls in alsamixer (terminal app) or in the Gnome Volume Control. Probably, you might find that one of the channels is muted.

---

### Post by mikewave on 2007-01-07
> **justifier said:**
> my advice would be to check all your sound drivers

And how is that done? I have a manual on Ubuntu which doesn't cover it.

---

### Post by mikewave on 2007-01-07
> **Lord Illidan said:**
> Check your volume controls in alsamixer (terminal app) or in the Gnome Volume Control. Probably, you might find that one of the channels is muted.

I just spent several minutes diddling with Alsamixer. I'm now listening to streaming radio (from WFMU.org FWIW) and everything's coming up stereo!

Thank all of you for responding to my question!

---

### Post by m0e on 2007-01-07
There is a problem with the drivers for M-Audio cards in Linux. For some reason after every reboot I have sound in only one channel until I move the Alsa volume control, then it works fine until reboot. I am running a M-Audio 7.1 Revolution on one of my boxes and have yet to find a better solution in the last 6-7 months since installing it.

---

### Post by faizal77 on 2007-08-25
**[COLOR="Red"][SIZE="4"]can somebody help me... i am using acer 4520 amd 64x2 turion realtex sound. iam using linux 7.04 for amd64bit. however the sound system not function. i cannot hear sound. [/SIZE][/COLOR]**

---

### Post by atasmrk on 2007-10-17
Sorry for bringing this thread from the dead, but I am also running into stereo trouble.

I can hear sound from one channel. I tried running alsamixer, but it reported "function snd_mixer_load failed: Invalid argument". Examining Sound preferences under System/Settings I noticed, that Mixer device is OSS based (unless I am mistaken) - Realtek ALC883 (OSS mixer). Every other setting is set to "autodetect", and test beeps regardless of the setting.

lsmod | grep snd outputs the following:

```
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  2 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  2 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
```

So I am pretty sure my system (Acer Aspire 5112WLMi) is using OSS instead of ALSA.

Any idea how to correct the problem?

---

