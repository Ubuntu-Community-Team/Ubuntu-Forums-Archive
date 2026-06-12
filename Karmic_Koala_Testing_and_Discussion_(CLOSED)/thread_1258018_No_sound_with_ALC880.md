---
title: "No sound with ALC880"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kozimodo on 2009-09-04
Since upgrading to karmic, sound has not worked. Alsa mixer brings up all the various controls, I have a systray volume icon that works but no sound emerges at all.  Any ideas?
```
$ sudo lspci -v -v -v
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: AOPEN Inc. Device 0569
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
$ lsmod|grep snd
snd_hda_codec_realtek   277732  1 
snd_hda_intel          31528  4 
snd_hda_codec          79776  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
```

---

### Post by taavikko on 2009-09-04
Check the output hardware in gnome-volume-manager
Put "gstreamer-properties" audio-output to autodetect

shutdown gdm and remove ~/.pulse* restart gdm, any change?

Does "aplay /usr/share/sounds/question.wav" bring in any noise?

Is some channel muted in mixer? "alsamixer" and "alsamixer -Dhw"

---

### Post by kozimodo on 2009-09-04
Turns out sound was muted and this showed in gnome-volume-control but didn't show in my tray-icon.  Everything works great now!  Thanks!

---

### Post by kozimodo on 2009-09-04
Hmmm, it doesn't seem to remember that it is unmuted when I reboot.

---

### Post by kozimodo on 2009-09-10
Uninstalled pulseaudio and sound works fine again.

---

