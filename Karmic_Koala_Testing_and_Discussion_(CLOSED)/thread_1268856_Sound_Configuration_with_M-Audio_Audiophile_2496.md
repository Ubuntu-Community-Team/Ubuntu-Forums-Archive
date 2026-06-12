---
title: "Sound Configuration with M-Audio Audiophile 2496"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by &gt;:3 on 2009-09-17
After Jaunty [COLOR="Blue"][refused to install]("http://ubuntuforums.org/showthread.php?t=1176026")[/COLOR] on my desktop, I'm now dualbooting Karmic & Hardy, and thought I'd try get a head-start on sorting out my sound. 

Currently, My sound works wonderfully on Hardy, Sound card is M-Audio Audiophile 2496, however, I didn't do the configuration, so I can't repeat it. 

Hardy output from: 
wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh

[http://www.alsa-project.org/db/?f=e10e9197e1757f4334bf8c1254ea01641fd2ff7e]("http://www.alsa-project.org/db/?f=e10e9197e1757f4334bf8c1254ea01641fd2ff7e")
```
!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Thu Sep 17 10:59:44 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 8.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.04.3 LTS"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.                
Product Name:      Dimension 5000               


!!Kernel Information
!!------------------

Kernel release:    2.6.24-16-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.16
Library version:    1.0.15
Utilities version:  1.0.15


!!Loaded ALSA modules
!!-------------------

snd_ice1712
snd_intel8x0


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

aRts:
      Installed - Yes (/usr/bin/artsd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xdca0, irq 20
 1 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1986 at irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
04:02.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1e.2 0401: 8086:266e (rev 03)
	Subsystem: 1028:0199
--
04:02.0 0401: 1412:1712 (rev 02)
	Subsystem: 1412:d634


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388


!!Loaded sound module options
!!--------------------------

!!Module: snd_ice1712
	cs8427_timeout : 500,500,500,500,500,500,500,500
	dxr_enable : 0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	omni : N,N,N,N,N,N,N,N

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : <NULL>
	buggy_irq : N
	buggy_semaphore : N
	enable : N
	id : <NULL>
	index : -1
	joystick : 0
	spdif_aclink : 0
	xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1986

PCI Subsys Vendor: 0x1028
PCI Subsys Device: 0x0199

Revision         : 0x02
Compat. Class    : 0x00
Subsys. Vendor ID: 0x0000
Subsys. ID       : 0x0000

Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         :  0dB [ 0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Double rate slots: 10/11
Extended ID      : codec=0 rev=2 AMAP LDAC SDAC CDAC DSA=0 DRA VRA
Extended status  : LDAC SDAC CDAC VRA
PCM front DAC    : 48000Hz
PCM Surr DAC     : 48000Hz
PCM LFE DAC      : 48000Hz
PCM ADC          : 48000Hz

                    Gain     Inverted  Buffer delay  Location
Master Out       :   0.0 dBV    -      16/fs         Rear I/O Panel
AUX Out          :   0.0 dBV    -      16/fs         Rear I/O Panel
Center/LFE Out   :   0.0 dBV    -      16/fs         Rear I/O Panel
Mic 1            :   0.0 dBV    -      16/fs         Rear I/O Panel
Mic 2            :   0.0 dBV    -      16/fs         Rear I/O Panel
Line In          :   0.0 dBV    -      16/fs         Rear I/O Panel



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0090
0:02 = 0000
0:04 = 0000
0:06 = 0006
0:08 = 0000
0:0a = 0000
0:0c = 801f
0:0e = 0000
0:10 = 0000
0:12 = 0000
0:14 = 0000
0:16 = 9f9f
0:18 = 0000
0:1a = 0404
0:1c = 0f0f
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0bc3
0:2a = 01f1
0:2c = bb80
0:2e = bb80
0:30 = bb80
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2000
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 8080
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 8080
0:6e = 8080
0:70 = 0000
0:72 = 0008
0:74 = 1201
0:76 = 7814
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5378
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Sep 17 11:55 /dev/snd/controlC0
crw-rw----  1 root audio 116, 32 Sep 17 11:55 /dev/snd/controlC1
crw-rw----  1 root audio 116,  8 Sep 17 11:55 /dev/snd/midiC0D0
crw-rw----  1 root audio 116, 24 Sep 17 11:55 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Sep 17 11:55 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 56 Sep 17 11:55 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116, 48 Sep 17 11:55 /dev/snd/pcmC1D0p
crw-rw----  1 root audio 116, 57 Sep 17 11:55 /dev/snd/pcmC1D1c
crw-rw----  1 root audio 116, 58 Sep 17 11:55 /dev/snd/pcmC1D2c
crw-rw----  1 root audio 116, 59 Sep 17 11:55 /dev/snd/pcmC1D3c
crw-rw----  1 root audio 116, 52 Sep 17 11:55 /dev/snd/pcmC1D4p
crw-rw----  1 root audio 116,  1 Sep 17 11:55 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Sep 17 11:55 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [M2496]

Card hw:0 'M2496'/'M Audio Audiophile 24/96 at 0xdca0, irq 20'
  Mixer name	: 'ICE1712 - multitrack'
  Components	: ''
  Controls      : 50
  Simple ctrls  : 29
Simple mixer control 'IEC958',0
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'IEC958 Multi',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 96 [100%] [on]
  Front Right: Capture 96 [100%] [on]
Simple mixer control 'IEC958 Multi',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 94 [98%] [on]
  Front Right: Capture 94 [98%] [on]
Simple mixer control 'IEC958',1
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'ADC',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 163
  Mono: 163 [100%] [18.00dB]
Simple mixer control 'ADC',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 163
  Mono: 163 [100%] [18.00dB]
Simple mixer control 'DAC',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 127
  Mono: 163 [128%] [18.00dB]
Simple mixer control 'DAC',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 127
  Mono: 163 [128%] [18.00dB]
Simple mixer control 'Deemphasis',0
  Capabilities: enum
  Items: '44.1kHz' 'Off' '48kHz' '32kHz'
  Item0: 'Off'
Simple mixer control 'H/W',0
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'Digital Mixer'
Simple mixer control 'H/W',1
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'Digital Mixer'
Simple mixer control 'H/W Multi',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 96 [100%] [0.00dB] [on]
  Front Right: Capture 96 [100%] [0.00dB] [on]
Simple mixer control 'H/W Multi',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 96 [100%] [0.00dB] [on]
  Front Right: Capture 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 96 [100%] [0.00dB] [on]
  Front Right: Playback 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi',1
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 96 [100%] [0.00dB] [on]
  Front Right: Playback 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi',2
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 96 [100%] [0.00dB] [on]
  Front Right: Playback 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi',3
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 96 [100%] [0.00dB] [on]
  Front Right: Playback 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi',4
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 96 [100%] [0.00dB] [on]
  Front Right: Playback 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi',5
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 96 [100%] [0.00dB] [on]
  Front Right: Playback 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi',6
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 96 [100%] [0.00dB] [on]
  Front Right: Playback 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi',7
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 96 [100%] [0.00dB] [on]
  Front Right: Playback 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi',8
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 96 [100%] [0.00dB] [on]
  Front Right: Playback 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi',9
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 96 [100%] [0.00dB] [on]
  Front Right: Playback 96 [100%] [0.00dB] [on]
Simple mixer control 'Multi Track Internal Clock',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000' 'IEC958 Input'
  Item0: '48000'
Simple mixer control 'Multi Track Internal Clock Default',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000'
  Item0: '44100'
Simple mixer control 'Multi Track Peak',0
  Capabilities: volume
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Capture channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Limits: 0 - 255
  Front Left: 0 [0%]
  Front Right: 0 [0%]
  Rear Left: 0 [0%]
  Rear Right: 0 [0%]
  Front Center: 0 [0%]
  Woofer: 0 [0%]
  Side Left: 0 [0%]
  Side Right: 0 [0%]
  Rear Center: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
Simple mixer control 'Multi Track Rate Locking',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Multi Track Rate Reset',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Multi Track Volume Rate',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 255 [100%]

!!-------Mixer controls for card 1 [ICH6]

Card hw:1 'ICH6'/'Intel ICH6 with AD1986 at irq 21'
  Mixer name	: 'Analog Devices AD1986'
  Components	: 'AC97a:41445378'
  Controls      : 44
  Simple ctrls  : 32
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [on]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [on]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Downmix',0
  Capabilities: enum
  Items: 'Off' '6 -> 4' '6 -> 2'
  Item0: 'Off'
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Front/Surround',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Mic/Line In',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Spread Front to Surround and Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'V_REFOUT',0
  Capabilities: enum
  Items: 'High-Z' '3.7 V' '2.25 V' '0 V'
  Item0: 'High-Z'


!!Alsactl output
!!-------------

--startcollapse--
state.M2496 {
	control.1 {
		comment.access read
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 255'
		iface PCM
		name 'IEC958 CS8427 Input Status'
		value 67
	}
	control.2 {
		comment.access read
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 255'
		iface PCM
		name 'IEC958 CS8427 Error Status'
		value 0
	}
	control.3 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		value ffffffffffffffffffffffffffffffffffffffffffffffff0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.4 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.5 {
		comment.access 'read write inactive'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback PCM Stream'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.6 {
		comment.access read
		comment.type BYTES
		comment.count 10
		iface PCM
		name 'IEC958 Q-subcode Capture Default'
		value '00000000000000000000'
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		value.0 true
		value.1 true
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 2
		value.0 true
		value.1 true
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 3
		value.0 true
		value.1 true
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 4
		value.0 true
		value.1 true
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 5
		value.0 true
		value.1 true
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 6
		value.0 true
		value.1 true
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 7
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 8
		value.0 true
		value.1 true
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 9
		value.0 true
		value.1 true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'Multi Playback Volume'
		value.0 96
		value.1 96
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'Multi Playback Volume'
		index 1
		value.0 96
		value.1 96
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'Multi Playback Volume'
		index 2
		value.0 96
		value.1 96
	}
	control.20 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'Multi Playback Volume'
		index 3
		value.0 96
		value.1 96
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'Multi Playback Volume'
		index 4
		value.0 96
		value.1 96
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'Multi Playback Volume'
		index 5
		value.0 96
		value.1 96
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'Multi Playback Volume'
		index 6
		value.0 96
		value.1 96
	}
	control.24 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'Multi Playback Volume'
		index 7
		value.0 96
		value.1 96
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'Multi Playback Volume'
		index 8
		value.0 96
		value.1 96
	}
	control.26 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'Multi Playback Volume'
		index 9
		value.0 96
		value.1 96
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		value.0 true
		value.1 true
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'IEC958 Multi Capture Switch'
		value.0 true
		value.1 true
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'IEC958 Multi Capture Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.31 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'H/W Multi Capture Volume'
		value.0 96
		value.1 96
	}
	control.32 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'H/W Multi Capture Volume'
		index 1
		value.0 96
		value.1 96
	}
	control.33 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'IEC958 Multi Capture Volume'
		value.0 96
		value.1 96
	}
	control.34 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'IEC958 Multi Capture Volume'
		index 1
		value.0 94
		value.1 94
	}
	control.35 {
		comment.access read
		comment.type BYTES
		comment.count 52
		iface CARD
		name 'ICE1712 EEPROM'
		value d63414121d011080720304fefb00000000000044040000000400000001000000000000000000000004000000fe000000fb000000
	}
	control.36 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '8000'
		comment.item.1 '9600'
		comment.item.2 '11025'
		comment.item.3 '12000'
		comment.item.4 '16000'
		comment.item.5 '22050'
		comment.item.6 '24000'
		comment.item.7 '32000'
		comment.item.8 '44100'
		comment.item.9 '48000'
		comment.item.10 '64000'
		comment.item.11 '88200'
		comment.item.12 '96000'
		comment.item.13 'IEC958 Input'
		iface MIXER
		name 'Multi Track Internal Clock'
		value '48000'
	}
	control.37 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '8000'
		comment.item.1 '9600'
		comment.item.2 '11025'
		comment.item.3 '12000'
		comment.item.4 '16000'
		comment.item.5 '22050'
		comment.item.6 '24000'
		comment.item.7 '32000'
		comment.item.8 '44100'
		comment.item.9 '48000'
		comment.item.10 '64000'
		comment.item.11 '88200'
		comment.item.12 '96000'
		iface MIXER
		name 'Multi Track Internal Clock Default'
		value '44100'
	}
	control.38 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Multi Track Rate Locking'
		value true
	}
	control.39 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Multi Track Rate Reset'
		value true
	}
	control.40 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'H/W Playback Route'
		value 'Digital Mixer'
	}
	control.41 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'H/W Playback Route'
		index 1
		value 'Digital Mixer'
	}
	control.42 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'IEC958 Playback Route'
		value 'PCM Out'
	}
	control.43 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'IEC958 Playback Route'
		index 1
		value 'PCM Out'
	}
	control.44 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 255'
		iface MIXER
		name 'Multi Track Volume Rate'
		value 255
	}
	control.45 {
		comment.access read
		comment.type INTEGER
		comment.count 22
		comment.range '0 - 255'
		iface MIXER
		name 'Multi Track Peak'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		value.8 0
		value.9 0
		value.10 0
		value.11 0
		value.12 0
		value.13 0
		value.14 0
		value.15 0
		value.16 0
		value.17 0
		value.18 0
		value.19 0
		value.20 0
		value.21 0
	}
	control.46 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'DAC Volume'
		value 163
	}
	control.47 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		iface MIXER
		name 'DAC Volume'
		index 1
		value 163
	}
	control.48 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 163'
		iface MIXER
		name 'ADC Volume'
		value 163
	}
	control.49 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 163'
		iface MIXER
		name 'ADC Volume'
		index 1
		value 163
	}
	control.50 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '44.1kHz'
		comment.item.1 Off
		comment.item.2 '48kHz'
		comment.item.3 '32kHz'
		iface MIXER
		name Deemphasis
		value Off
	}
}
state.ICH6 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Master Playback Volume'
		value.0 31
		value.1 31
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Center Playback Volume'
		value 31
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'LFE Playback Volume'
		value 31
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Surround Playback Volume'
		value.0 31
		value.1 31
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 31
		value.1 31
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value true
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Master Mono Playback Volume'
		value 25
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Speaker Playback Switch'
		value true
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name 'PC Speaker Playback Volume'
		value 15
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value false
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Phone Playback Volume'
		value 0
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 true
		value.1 true
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Mic Playback Volume'
		value.0 31
		value.1 31
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost ( 20dB)'
		value false
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Line Playback Volume'
		value.0 31
		value.1 31
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'CD Playback Volume'
		value.0 31
		value.1 31
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Playback Switch'
		value.0 false
		value.1 false
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
	}
	control.27 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'PCM Playback Volume'
		value.0 31
		value.1 31
	}
	control.28 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Line
		value.1 Line
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.30 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		iface MIXER
		name 'Capture Volume'
		value.0 15
		value.1 15
	}
	control.31 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.32 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.33 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Stereo Mic'
		value false
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Exchange Center/LFE'
		value false
	}
	control.35 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Exchange Front/Surround'
		value false
	}
	control.36 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Exchange Mic/Line In'
		value false
	}
	control.37 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Spread Front to Surround and Center/LFE'
		value false
	}
	control.38 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 '6 -> 4'
		comment.item.2 '6 -> 2'
		iface MIXER
		name Downmix
		value Off
	}
	control.39 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 High-Z
		comment.item.1 '3.7 V'
		comment.item.2 '2.25 V'
		comment.item.3 '0 V'
		iface MIXER
		name V_REFOUT
		value High-Z
	}
	control.40 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Shared
		comment.item.1 Independent
		iface MIXER
		name 'Surround Jack Mode'
		value Shared
	}
	control.41 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '2ch'
		comment.item.1 '4ch'
		comment.item.2 '6ch'
		iface MIXER
		name 'Channel Mode'
		value '2ch'
	}
	control.42 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Jack Sense'
		value false
	}
	control.43 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Jack Sense'
		value false
	}
	control.44 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_intel8x0
snd_ice1712
snd_ice17xx_ak4xxx
snd_ak4xxx_adda
snd_cs8427
snd_ac97_codec
ac97_bus
snd_i2c
snd_mpu401_uart
snd_pcm_oss
snd_pcm
snd_page_alloc
snd_mixer_oss
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
af_packet
i915
drm
binfmt_misc
rfcomm
l2cap
bluetooth
ppdev
ipv6
speedstep_lib
cpufreq_userspace
cpufreq_ondemand
cpufreq_powersave
cpufreq_conservative
cpufreq_stats
freq_table
video
output
container
sbs
sbshc
dock
battery
iptable_filter
ip_tables
x_tables
aes_i586
dm_crypt
dm_mod
ac
ndiswrapper
lp
joydev
psmouse
serio_raw
button
intel_agp
shpchp
parport_pc
parport
dcdbas
agpgart
pci_hotplug
iTCO_wdt
iTCO_vendor_support
evdev
pcspkr
ext3
jbd
mbcache
sg
sr_mod
cdrom
sd_mod
usbhid
hid
ata_piix
pata_acpi
b44
ata_generic
ssb
mii
libata
scsi_mod
ehci_hcd
uhci_hcd
usbcore
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
fuse


!!ALSA/HDA dmesg
!!------------------




```

I'm attempting to replicate these settings in Karmic, but with little success

My Current situation:
[http://www.alsa-project.org/db/?f=2ba48974fa7ed95ddb91d0a9c1e2710b85f9cb5c]("http://www.alsa-project.org/db/?f=2ba48974fa7ed95ddb91d0a9c1e2710b85f9cb5c")

```
!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Thu Sep 17 17:03:45 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu karmic (development branch) \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu karmic (development branch)"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.                
Product Name:      Dimension 5000               


!!Kernel Information
!!------------------

Kernel release:    2.6.31-10-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_intel8x0
snd_ice1712


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1986 at irq 23
 1 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xdca0, irq 18


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
04:02.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1e.2 0401: 8086:266e (rev 03)
	Subsystem: 1028:0199
--
04:02.0 0401: 1412:1712 (rev 02)
	Subsystem: 1412:d634


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : <NULL>
	buggy_irq : N
	buggy_semaphore : N
	enable : N
	id : <NULL>
	index : -1
	joystick : 0
	spdif_aclink : 0
	xbox : N

!!Module: snd_ice1712
	cs8427_timeout : 500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500,500
	dxr_enable : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	omni : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1986

PCI Subsys Vendor: 0x1028
PCI Subsys Device: 0x0199

Flags: 30
Revision         : 0x02
Compat. Class    : 0x00
Subsys. Vendor ID: 0x0000
Subsys. ID       : 0x0000

Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         :  0dB [ 0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Double rate slots: 10/11
Extended ID      : codec=0 rev=2 AMAP LDAC SDAC CDAC DSA=0 DRA VRA
Extended status  : LDAC SDAC CDAC VRA
PCM front DAC    : 44100Hz
PCM Surr DAC     : 44100Hz
PCM LFE DAC      : 44100Hz
PCM ADC          : 44100Hz

                    Gain     Inverted  Buffer delay  Location
Master Out       :   0.0 dBV    -      16/fs         Rear I/O Panel
AUX Out          :   0.0 dBV    -      16/fs         Rear I/O Panel
Center/LFE Out   :   0.0 dBV    -      16/fs         Rear I/O Panel
Mic 1            :   0.0 dBV    -      16/fs         Rear I/O Panel
Mic 2            :   0.0 dBV    -      16/fs         Rear I/O Panel
Line In          :   0.0 dBV    -      16/fs         Rear I/O Panel



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0090
0:02 = 9f9f
0:04 = 8080
0:06 = 801f
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 9f9f
0:10 = 9f9f
0:12 = 0606
0:14 = 0000
0:16 = 9f9f
0:18 = 8888
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0bc3
0:2a = 01f1
0:2c = ac44
0:2e = ac44
0:30 = ac44
0:32 = ac44
0:34 = 0000
0:36 = 8080
0:38 = 8080
0:3a = 2000
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 8080
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 8080
0:6e = 8080
0:70 = 0000
0:72 = 0000
0:74 = 1201
0:76 = 7814
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5378
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 10 Sep 17 12:16 /dev/snd/controlC0
crw-rw----  1 root audio 116, 14 Sep 17 12:16 /dev/snd/controlC1
crw-rw----  1 root audio 116, 11 Sep 17 12:16 /dev/snd/midiC1D0
crw-rw----  1 root audio 116,  9 Sep 17 12:16 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  8 Sep 17 12:16 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  7 Sep 17 12:16 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  6 Sep 17 12:16 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116,  5 Sep 17 12:16 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116,  4 Sep 17 12:16 /dev/snd/pcmC0D4p
crw-rw----  1 root audio 116, 13 Sep 17 18:02 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116, 12 Sep 17 12:16 /dev/snd/pcmC1D0p
crw-rw----  1 root audio 116,  3 Sep 17 12:16 /dev/snd/seq
crw-rw----  1 root audio 116,  2 Sep 17 12:16 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Sep 17 12:16 .
drwxr-xr-x 3 root root 320 Sep 17 12:16 ..
lrwxrwxrwx 1 root root  12 Sep 17 12:16 pci-0000:00:1e.2 -> ../controlC0
lrwxrwxrwx 1 root root  12 Sep 17 12:16 pci-0000:04:02.0 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [ICH6]

Card hw:0 'ICH6'/'Intel ICH6 with AD1986 at irq 23'
  Mixer name	: 'Analog Devices AD1986'
  Components	: 'AC97a:41445378'
  Controls      : 44
  Simple ctrls  : 32
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [off]
  Front Right: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [off]
  Front Right: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [on]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [on]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Downmix',0
  Capabilities: enum
  Items: 'Off' '6 -> 4' '6 -> 2'
  Item0: 'Off'
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Front/Surround',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Mic/Line In',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Spread Front to Surround and Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'V_REFOUT',0
  Capabilities: enum
  Items: 'High-Z' '3.7 V' '2.25 V' '0 V'
  Item0: 'High-Z'

!!-------Mixer controls for card 1 [M2496]

Card hw:1 'M2496'/'M Audio Audiophile 24/96 at 0xdca0, irq 18'
  Mixer name	: 'ICE1712 - multitrack'
  Components	: ''
  Controls      : 50
  Simple ctrls  : 29
Simple mixer control 'IEC958',0
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'IEC958 Multi',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'IEC958 Multi',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'IEC958',1
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'ADC',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 163
  Mono: 102 [63%] [-12.50dB]
Simple mixer control 'ADC',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 163
  Mono: 102 [63%] [-12.50dB]
Simple mixer control 'DAC',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 127
  Mono: 102 [80%] [-12.50dB]
Simple mixer control 'DAC',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 127
  Mono: 102 [80%] [-12.50dB]
Simple mixer control 'Deemphasis',0
  Capabilities: enum
  Items: '44.1kHz' 'Off' '48kHz' '32kHz'
  Item0: 'Off'
Simple mixer control 'H/W',0
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'H/W',1
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'H/W Multi',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'H/W Multi',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',1
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',2
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',3
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',4
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',5
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',6
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',7
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',8
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',9
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi Track Internal Clock',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000' 'IEC958 Input'
  Item0: '44100'
Simple mixer control 'Multi Track Internal Clock Default',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000'
  Item0: '44100'
Simple mixer control 'Multi Track Peak',0
  Capabilities: volume
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Capture channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Limits: 0 - 255
  Front Left: 0 [0%]
  Front Right: 0 [0%]
  Rear Left: 0 [0%]
  Rear Right: 0 [0%]
  Front Center: 0 [0%]
  Woofer: 0 [0%]
  Side Left: 0 [0%]
  Side Right: 0 [0%]
  Rear Center: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
Simple mixer control 'Multi Track Rate Locking',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Multi Track Rate Reset',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Multi Track Volume Rate',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 48 [19%]


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 false
		value.1 false
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 0
		value.1 0
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value false
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 31
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 31
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 false
		value.1 false
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 31
		value.1 31
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 31
		value.1 31
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 0
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Speaker Playback Switch'
		value false
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'PC Speaker Playback Volume'
		value 0
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value false
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Phone Playback Volume'
		value 0
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost ( 20dB)'
		value false
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Playback Switch'
		value.0 false
		value.1 false
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Playback Switch'
		value.0 false
		value.1 false
	}
	control.27 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 23
		value.1 23
	}
	control.28 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Mic
		value.1 Mic
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.30 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.31 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.32 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.33 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Stereo Mic'
		value false
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Exchange Center/LFE'
		value false
	}
	control.35 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Exchange Front/Surround'
		value false
	}
	control.36 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Exchange Mic/Line In'
		value false
	}
	control.37 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Spread Front to Surround and Center/LFE'
		value false
	}
	control.38 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 '6 -> 4'
		comment.item.2 '6 -> 2'
		iface MIXER
		name Downmix
		value Off
	}
	control.39 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 High-Z
		comment.item.1 '3.7 V'
		comment.item.2 '2.25 V'
		comment.item.3 '0 V'
		iface MIXER
		name V_REFOUT
		value High-Z
	}
	control.40 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Shared
		comment.item.1 Independent
		iface MIXER
		name 'Surround Jack Mode'
		value Shared
	}
	control.41 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '2ch'
		comment.item.1 '4ch'
		comment.item.2 '6ch'
		iface MIXER
		name 'Channel Mode'
		value '2ch'
	}
	control.42 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Jack Sense'
		value false
	}
	control.43 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Jack Sense'
		value false
	}
	control.44 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
}
state.M2496 {
	control.1 {
		comment.access read
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 255'
		iface PCM
		name 'IEC958 CS8427 Input Status'
		value 67
	}
	control.2 {
		comment.access read
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 255'
		iface PCM
		name 'IEC958 CS8427 Error Status'
		value 0
	}
	control.3 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		value ffffffffffffffffffffffffffffffffffffffffffffffff0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.4 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.5 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback PCM Stream'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.6 {
		comment.access read
		comment.type BYTES
		comment.count 10
		iface PCM
		name 'IEC958 Q-subcode Capture Default'
		value '00000000000000000000'
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		value.0 false
		value.1 false
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 2
		value.0 false
		value.1 false
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 3
		value.0 false
		value.1 false
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 4
		value.0 false
		value.1 false
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 5
		value.0 false
		value.1 false
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 6
		value.0 false
		value.1 false
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 7
		value.0 false
		value.1 false
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 8
		value.0 false
		value.1 false
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Multi Playback Switch'
		index 9
		value.0 false
		value.1 false
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		value.0 0
		value.1 0
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 2
		value.0 0
		value.1 0
	}
	control.20 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 3
		value.0 0
		value.1 0
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 4
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 5
		value.0 0
		value.1 0
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 6
		value.0 0
		value.1 0
	}
	control.24 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 7
		value.0 0
		value.1 0
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 8
		value.0 0
		value.1 0
	}
	control.26 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'Multi Playback Volume'
		index 9
		value.0 0
		value.1 0
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		value.0 false
		value.1 false
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'H/W Multi Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'IEC958 Multi Capture Switch'
		value.0 false
		value.1 false
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'IEC958 Multi Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.31 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'H/W Multi Capture Volume'
		value.0 0
		value.1 0
	}
	control.32 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		comment.dbmin -14400
		comment.dbmax 0
		iface MIXER
		name 'H/W Multi Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.33 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'IEC958 Multi Capture Volume'
		value.0 0
		value.1 0
	}
	control.34 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 96'
		iface MIXER
		name 'IEC958 Multi Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.35 {
		comment.access read
		comment.type BYTES
		comment.count 52
		iface CARD
		name 'ICE1712 EEPROM'
		value d63414121d011080720304fefb00000000000044040000000400000001000000000000000000000004000000fe000000fb000000
	}
	control.36 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '8000'
		comment.item.1 '9600'
		comment.item.2 '11025'
		comment.item.3 '12000'
		comment.item.4 '16000'
		comment.item.5 '22050'
		comment.item.6 '24000'
		comment.item.7 '32000'
		comment.item.8 '44100'
		comment.item.9 '48000'
		comment.item.10 '64000'
		comment.item.11 '88200'
		comment.item.12 '96000'
		comment.item.13 'IEC958 Input'
		iface MIXER
		name 'Multi Track Internal Clock'
		value '44100'
	}
	control.37 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '8000'
		comment.item.1 '9600'
		comment.item.2 '11025'
		comment.item.3 '12000'
		comment.item.4 '16000'
		comment.item.5 '22050'
		comment.item.6 '24000'
		comment.item.7 '32000'
		comment.item.8 '44100'
		comment.item.9 '48000'
		comment.item.10 '64000'
		comment.item.11 '88200'
		comment.item.12 '96000'
		iface MIXER
		name 'Multi Track Internal Clock Default'
		value '44100'
	}
	control.38 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Multi Track Rate Locking'
		value false
	}
	control.39 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Multi Track Rate Reset'
		value true
	}
	control.40 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'H/W Playback Route'
		value 'PCM Out'
	}
	control.41 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'H/W Playback Route'
		index 1
		value 'PCM Out'
	}
	control.42 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'IEC958 Playback Route'
		value 'PCM Out'
	}
	control.43 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'H/W In 2'
		comment.item.4 'H/W In 3'
		comment.item.5 'H/W In 4'
		comment.item.6 'H/W In 5'
		comment.item.7 'H/W In 6'
		comment.item.8 'H/W In 7'
		comment.item.9 'IEC958 In L'
		comment.item.10 'IEC958 In R'
		comment.item.11 'Digital Mixer'
		iface MIXER
		name 'IEC958 Playback Route'
		index 1
		value 'PCM Out'
	}
	control.44 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 255'
		iface MIXER
		name 'Multi Track Volume Rate'
		value 48
	}
	control.45 {
		comment.access read
		comment.type INTEGER
		comment.count 22
		comment.range '0 - 255'
		iface MIXER
		name 'Multi Track Peak'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		value.8 0
		value.9 0
		value.10 0
		value.11 0
		value.12 0
		value.13 0
		value.14 0
		value.15 0
		value.16 0
		value.17 0
		value.18 0
		value.19 0
		value.20 0
		value.21 0
	}
	control.46 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		comment.dbmin -6350
		comment.dbmax 0
		iface MIXER
		name 'DAC Volume'
		value 102
	}
	control.47 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		comment.dbmin -6350
		comment.dbmax 0
		iface MIXER
		name 'DAC Volume'
		index 1
		value 102
	}
	control.48 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 163'
		comment.dbmin -6350
		comment.dbmax 1800
		iface MIXER
		name 'ADC Volume'
		value 102
	}
	control.49 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 163'
		comment.dbmin -6350
		comment.dbmax 1800
		iface MIXER
		name 'ADC Volume'
		index 1
		value 102
	}
	control.50 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '44.1kHz'
		comment.item.1 Off
		comment.item.2 '48kHz'
		comment.item.3 '32kHz'
		iface MIXER
		name Deemphasis
		value Off
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_ice1712
snd_ice17xx_ak4xxx
snd_ak4xxx_adda
snd_cs8427
snd_i2c
snd_mpu401_uart
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
fbcon
tileblit
font
bitblit
softcursor
binfmt_misc
psmouse
serio_raw
i915
drm
i2c_algo_bit
dell_wmi
video
intel_agp
dcdbas
output
agpgart
ppdev
parport_pc
ndiswrapper
joydev
lp
parport
hid_cherry
usbhid
b44
ssb
mii
dm_raid45
xor


!!ALSA/HDA dmesg
!!------------------


```

I appreciate that Karmic is only for testing purposes, and It's not my main OS, but I'd be ecstatic if I could sort it!

---

### Post by ianc on 2009-09-17
Partial solution (but adequate for my purposes) here:

[http://www.pulseaudio.org/ticket/624](http://www.pulseaudio.org/ticket/624)

---

### Post by &gt;:3 on 2009-09-17
> **ianc said:**
> Partial solution (but adequate for my purposes) here:

[http://www.pulseaudio.org/ticket/624](http://www.pulseaudio.org/ticket/624)

Is [http://www.pulseaudio.org/attachment/ticket/624/pulseaudio-add-profile-sets-for-M_Audio-Audiophile-2496.patch]("http://www.pulseaudio.org/attachment/ticket/624/pulseaudio-add-profile-sets-for-M_Audio-Audiophile-2496.patch") the solution? Great! How do you apply it?

---

### Post by ianc on 2009-09-17
Edit /lib/udev/rules.d/90-pulseaudio.rules and add the line:

```
SUBSYSTEMS=="pci", ATTRS{vendor}=="0x1412", ATTRS{device}=="0x1712", ATTRS{subsystem_vendor}=="0x1412", ATTRS{subsystem_device}=="0xd634", ENV{PULSE_PROFILE_SET}="m_audio-audiophile-2496.conf"
```

Create /usr/share/pulseaudio/alsa-mixer/profile-sets/m_audio-audiophile-2496.conf:

```
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2.1 of the
# License, or (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

; M-Audio Delta Audiophile 2496
;
; This card, based on the Via ICE1712 chipset, has two stereo audio channels
; (1 in and 1 out) and a separate S/PDIF digital stereo channel. Like with
; all ICE1712-based cards, this is exposed by ALSA as a single 10-channel
; device with some of the channels not connected.
;
; See default.conf for an explanation on the directives used here.

[General]
auto-profiles = no

[Mapping analog-stereo-in]
description = Analog Stereo Input
device-strings = hw:%f,0
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
direction = input

[Mapping analog-stereo-out]
description = Analog Stereo Output
device-strings = hw:%f,0
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
direction = output

[Mapping analog-digital-stereo-out]
description = Analog/Digital Stereo Output
device-strings = hw:%f,0
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,front-left,front-right
direction = output

[Mapping digital-stereo-out]
description = Digital Stereo Output
device-strings = hw:%f,0
channel-map = aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,front-left,front-right
direction = output

[Mapping digital-stereo-in]
description = Digital Stereo Input
device-strings = hw:%f,0
channel-map = front-left,front-right,front-left,front-right,front-left,front-right,front-left,front-right,front-left,front-right,front-left,front-right
direction = input

[Mapping digital-stereo]
description = Digital Stereo Input/Output
#device-strings = hw:%f,1
device-strings = iec958:%f
channel-map = left,right
direction = any

[Profile output:stereo]
description = Analog Stereo Output
output-mappings = analog-stereo-out
input-mappings =
priority = 80
skip-probe = yes

[Profile output:stereo-da+input:stereo-analog]
description = Analog Stereo Input/Output
output-mappings = analog-stereo-out
input-mappings = analog-stereo-in
priority = 100
skip-probe = yes

[Profile output:stereo-da+input:stereo-analog]
description = Analog Stereo Input/Output, Digital Stereo Output
output-mappings = analog-digital-stereo-out
input-mappings = analog-stereo-in
priority = 90
skip-probe = yes

[Profile output:spdif]
description = Digital Stereo Output (Analog Disabled)
output-mappings = digital-stereo-out
input-mappings = 
priority = 60
skip-probe = yes

[Profile output:spdif+input:spdif]
description = Digital Stereo Input/Output (Analog Disabled)
output-mappings = digital-stereo-out
input-mappings = digital-stereo-in
priority = 70
skip-probe = yes

```

Then restart - hopefully it should then work...

---

### Post by &gt;:3 on 2009-09-17
Brilliant it works Great, Thanks!

---

### Post by ianc on 2009-09-18
One thing I forgot to mention.

Pulseaudio updates (one just arrived here) usually overwrite /lib/udev/rules.d/90-pulseaudio.rules - so if you find that it stops working it's worth checking this file and modifying it again if necessary.

I keep a copy of the modified file handy so that when this happens all I have to is cp it into the correct folder.

---

### Post by &gt;:3 on 2009-09-18
Thanks, I'll do the same.

---

### Post by fuxialis on 2009-10-22
Thank You. Solution works great!

---

### Post by RMFROTA on 2009-10-24
I just migrate from UBUNTU 9.04 to 9.10 and everything works perfect, except my AUDIOPHILE sound card. Now it is all working. THANK YOU SO MUCH!!!!

---

