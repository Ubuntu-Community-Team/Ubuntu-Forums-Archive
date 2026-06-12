---
title: "kubuntu intrepid: No sound with nVidia MCP73"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eantoranz on 2008-10-10
I'm on kubuntu intrepid and I have no sound with this nVidia MCP73 card. What should I do?

for example:
```

$ mplayer Música/El\ Cuarteto/Caballo\ Viejo.mp3                                               
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team                                                                  
CPU: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)                        
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Música/El Cuarteto/Caballo Viejo.mp3.
Audio file file format detected.
Clip info:
 Title: Caballo Viejo
 Artist: El Cuarteto
 Album: 20 &#65533;xitos de El Cuarteto
 Year: 0
 Comment:
 Track: 20
 Genre: Unknown
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Permission denied
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
mcop warning: user defined signal handler found for SIG_PIPE, overriding
[AO ARTS] Connected to sound server.
[AO ARTS] Stream opened.
[AO ARTS] buffer size: 20480
[AO ARTS] buffer size: 2048
AO: [arts] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   2.0 (02.0) of 337.0 (05:37.0)  1.0%

MPlayer interrupted by signal 2 in module: play_audio

```

What should i do?

---

### Post by eantoranz on 2008-10-10
```

$ sudo lspci
[sudo] password for edmundo:
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.3 Co-processor: nVidia Corporation MCP73 Co-processor (rev a2)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP73 SATA RAID Controller (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100 / nForce 620i (rev a2)
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

```

---

### Post by jynyl on 2008-10-25
Similar issue here - KDE notifications give sound ok, but mplayer, amarok, kmplayer, etc are silent.
Kubuntu 8.10 rc1
audio device: Intel 82801G (ICH7 family)

Is this a bug, or is there some config I need to set?

TIA

Peter

UPDATE: fixed by adjusting PCM setting in Mixer off 0
(Click on the speaker icon in the panel, slide PCM up to 80 or whatever.)

---

### Post by Dareus on 2008-10-25
I have a different problem: mplayer sounds fine but neither juk nor amarok are able to play any sound. Kde notifications aren't working as well even if i can play those sounds with mplayer.

I think this issue is somewhat related to phonon

---

### Post by eantoranz on 2008-10-25
Well.... I can tell you that since yesterday (I guess after a kernel update) I was able to get sound. I just set everything to use alsa (default device on the sound configuration). Does it work for you that way?

---

