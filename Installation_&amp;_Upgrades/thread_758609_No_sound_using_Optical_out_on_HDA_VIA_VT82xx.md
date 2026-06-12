---
title: "No sound using Optical out on HDA VIA VT82xx"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by kingu on 2008-04-18
Hi

Using hardy beta 4 the sound worked flawlessly on my friends VIA Epia EX15000, but after some opgrades released between april 2nd and 9th the optical output ceased to work. 

There is however sound through the analog connection, but his surround sound does not have input for the analog. 

Does anyone have an idea on how to fix it?

Here below is the output from the alsa-info.sh script with working sound on the live-cd. Below that the output on the non-working system.

```
name=root&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=
!!################################
!!ALSA Information Script v 0.4.41
!!################################

!!Script ran on: Fri Apr 18 10:34:22 UTC 2008


!!Linux Distribution
!!------------------

Ubuntu hardy (development branch) \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu hardy (development branch)"


!!Kernel Information
!!------------------

Kernel release:    2.6.24-12-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.16
Library version:    
Utilities version:  1.0.15


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xdfefc000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

02:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

02:01.0 0403: 1106:3288 (rev 10)
	Subsystem: 1106:aa09


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

!!Module: snd_hda_intel
enable : Y,Y,Y,Y,Y,Y,Y,Y
enable_msi : 0
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
index : -1,-1,-1,-1,-1,-1,-1,-1
model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
position_fix : 0,0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: VIA VIA VT1708
Address: 0
Vendor Id: 0x11061708
Subsystem Id: 0x11060300
Revision Id: 0x100500
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x10 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x13 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x14 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x5]: PCM AC3
Node 0x15 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x14, stepsize=0x06, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x440]: 48000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x16 [Audio Input] wcaps 0x100311: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital: Validity
  Digital category: 0x0
  PCM:
    rates [0x1f0]: 32000 44100 48000 88200 96000
    bits [0xa]: 16 24
    formats [0x5]: PCM AC3
  Connection: 1
     0x26
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x06, mute=1
  Amp-In vals:  [0x1f 0x1f] [0x19 0x19] [0x80 0x80] [0x00 0x00] [0x00 0x00] [0x80 0x80]
  Connection: 6
     0x10 0x24 0x1d 0x1e 0x21 0x13
Node 0x18 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 5
     0x17* 0x24 0x1d 0x1e 0x21
Node 0x19 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x11
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x12
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x13
Node 0x1c [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081c: OUT HP Detect
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x19
Node 0x1d [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x08334: IN OUT Detect
    Vref caps: HIZ 50
  Pin Default 0x01a19026: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x6
  Pin-ctls: 0x21: IN VREF_50
  Connection: 1
     0x1a
Node 0x1e [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x08334: IN OUT Detect
    Vref caps: HIZ 50
  Pin Default 0x0181302e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0xe
  Pin-ctls: 0x20: IN VREF_HIZ
  Connection: 1
     0x19
Node 0x1f [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x16 0x16]
  Pincap 0x081c: OUT HP Detect
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x17
Node 0x20 [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x13 0x13]
  Pincap 0x081c: OUT HP Detect
  Pin Default 0x022140f0: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Connection: 1
     0x17
Node 0x21 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x08334: IN OUT Detect
    Vref caps: HIZ 50
  Pin Default 0x02a190f0: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Connection: 1
     0x1b
Node 0x22 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x0814: OUT Detect
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x1a
Node 0x23 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x0814: OUT Detect
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x1b
Node 0x24 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x99330127: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x7
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x25 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x074411f0: [Jack] SPDIF Out at Ext Rear Panel
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x14
Node 0x26 [Pin Complex] wcaps 0x400201: Stereo Digital
  Pincap 0x0810030: IN OUT EAPD
  EAPD 0x0:
  Pin Default 0x07c421f0: [Jack] SPDIF In at Ext Rear Panel
    Conn = RCA, Color = Grey
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x27 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x14, stepsize=0x06, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x440]: 48000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 2008-04-18 10:30 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 2008-04-18 10:30 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 24 2008-04-18 10:31 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 2008-04-18 10:33 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 25 2008-04-18 10:30 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116, 17 2008-04-18 10:30 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  1 2008-04-18 10:30 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 2008-04-18 10:30 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: VT1708 Digital [VT1708 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: VT82xx [HDA VIA VT82xx], device 1: VT1708 Digital [VT1708 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [VT82xx]

Simple mixer control 'Master Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [14.00dB] [on]
  Front Right: Playback 31 [100%] [14.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 19 [70%] [-14.00dB] [on]
  Front Right: Playback 19 [70%] [-14.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 22 [81%] [-8.75dB] [on]
  Front Right: Playback 22 [81%] [-8.75dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-40.25dB] [on]
  Front Right: Playback 0 [0%] [-40.25dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 0 [0%] [-47.25dB] [on]
  Front Right: Playback 0 [0%] [-47.25dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 27
  Mono: Playback 0 [0%] [-47.25dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 27
  Mono: Playback 0 [0%] [-47.25dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 0 [0%] [-47.25dB] [on]
  Front Right: Playback 0 [0%] [-47.25dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-40.25dB] [on]
  Front Right: Playback 0 [0%] [-40.25dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.50dB] [on]
  Front Right: Playback 25 [81%] [3.50dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-40.25dB] [off]
  Front Right: Playback 0 [0%] [-40.25dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Stereo Mixer'


!!Alsactl output
!!-------------

--startcollapse--
state.VT82xx {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Master Front Playback Volume'
		value.0 31
		value.1 31
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 27'
		iface MIXER
		name 'Front Playback Volume'
		value.0 22
		value.1 22
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 27'
		iface MIXER
		name 'Surround Playback Volume'
		value.0 0
		value.1 0
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 27'
		iface MIXER
		name 'Center Playback Volume'
		value 0
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 27'
		iface MIXER
		name 'LFE Playback Volume'
		value 0
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 27'
		iface MIXER
		name 'Side Playback Volume'
		value.0 0
		value.1 0
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Side Playback Switch'
		value.0 true
		value.1 true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 27'
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 19
		value.1 19
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 true
		value.1 true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
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
		name 'CD Playback Volume'
		value.0 25
		value.1 25
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
		comment.range '0 - 20'
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 20'
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.27 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Stereo Mixer'
		comment.item.1 Mic
		comment.item.2 'Front Mic'
		comment.item.3 Line
		comment.item.4 CD
		iface MIXER
		name 'Input Source'
		value 'Stereo Mixer'
	}
	control.28 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.29 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.30 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.32 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
	}
	control.33 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.34 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
reiserfs
via
drm
ipv6
af_packet
rfcomm
l2cap
bluetooth
ppdev
parport_pc
lp
parport
acpi_cpufreq
cpufreq_userspace
cpufreq_stats
cpufreq_powersave
cpufreq_ondemand
freq_table
cpufreq_conservative
video
output
sbs
sbshc
container
dock
ac
iptable_filter
ip_tables
x_tables
snd_hda_intel
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_page_alloc
snd_hwdep
snd_seq_dummy
evdev
snd_seq_oss
psmouse
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
serio_raw
snd_seq
snd_timer
snd_seq_device
snd
soundcore
pcspkr
button
i2c_viapro
i2c_core
shpchp
pci_hotplug
via_agp
agpgart
battery
squashfs
loop
unionfs
nls_cp437
isofs
usbhid
hid
ide_disk
ide_cd
cdrom
pata_via
pata_acpi
ata_generic
libata
scsi_mod
ohci1394
ieee1394
via_rhine
mii
ehci_hcd
uhci_hcd
usbcore
via82cxxx
ide_core
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
fuse

```

```
!!################################
!!ALSA Information Script v 0.4.41
!!################################

!!Script ran on: Fri Apr 18 12:50:58 CEST 2008


!!Linux Distribution
!!------------------

Ubuntu 8.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.04"


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
Library version:    
Utilities version:  1.0.15


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xdfefc000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

02:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

02:01.0 0403: 1106:3288 (rev 10)
	Subsystem: 1106:aa09


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

!!Module: snd_hda_intel
enable : Y,Y,Y,Y,Y,Y,Y,Y
enable_msi : 0
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
index : -1,-1,-1,-1,-1,-1,-1,-1
model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
position_fix : 0,0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: VIA VIA VT1708
Address: 0
Vendor Id: 0x11061708
Subsystem Id: 0x11060300
Revision Id: 0x100500
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x10 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x13 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x14 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital: Enabled Copyright Non-Audio GenLevel
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x5]: PCM AC3
Node 0x15 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x14, stepsize=0x06, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x440]: 48000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x16 [Audio Input] wcaps 0x100311: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital: Validity
  Digital category: 0x0
  PCM:
    rates [0x1f0]: 32000 44100 48000 88200 96000
    bits [0xa]: 16 24
    formats [0x5]: PCM AC3
  Connection: 1
     0x26
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x06, mute=1
  Amp-In vals:  [0x17 0x17] [0x19 0x19] [0x80 0x80] [0x14 0x14] [0x17 0x17] [0x80 0x80]
  Connection: 6
     0x10 0x24 0x1d 0x1e 0x21 0x13
Node 0x18 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 5
     0x17* 0x24 0x1d 0x1e 0x21
Node 0x19 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x15 0x15]
  Connection: 1
     0x11
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x16]
  Connection: 1
     0x12
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Connection: 1
     0x13
Node 0x1c [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081c: OUT HP Detect
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x19
Node 0x1d [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x08334: IN OUT Detect
    Vref caps: HIZ 50
  Pin Default 0x01a19026: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x6
  Pin-ctls: 0x21: IN VREF_50
  Connection: 1
     0x1a
Node 0x1e [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x08334: IN OUT Detect
    Vref caps: HIZ 50
  Pin Default 0x0181302e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0xe
  Pin-ctls: 0x20: IN VREF_HIZ
  Connection: 1
     0x19
Node 0x1f [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Pincap 0x081c: OUT HP Detect
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x17
Node 0x20 [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Pincap 0x081c: OUT HP Detect
  Pin Default 0x022140f0: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Connection: 1
     0x17
Node 0x21 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x08334: IN OUT Detect
    Vref caps: HIZ 50
  Pin Default 0x02a190f0: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Connection: 1
     0x1b
Node 0x22 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x0814: OUT Detect
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x1a
Node 0x23 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x0814: OUT Detect
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x1b
Node 0x24 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x99330127: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x7
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x25 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x074411f0: [Jack] SPDIF Out at Ext Rear Panel
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x14
Node 0x26 [Pin Complex] wcaps 0x400201: Stereo Digital
  Pincap 0x0810030: IN OUT EAPD
  EAPD 0x0:
  Pin Default 0x07c421f0: [Jack] SPDIF In at Ext Rear Panel
    Conn = RCA, Color = Grey
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x27 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x14, stepsize=0x06, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x440]: 48000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 2008-04-18 12:49 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 2008-04-18 12:49 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 24 2008-04-18 12:49 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 2008-04-18 12:50 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 25 2008-04-18 12:49 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116, 17 2008-04-18 12:49 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  1 2008-04-18 12:49 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 2008-04-18 12:49 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: VT1708 Digital [VT1708 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: VT82xx [HDA VIA VT82xx], device 1: VT1708 Digital [VT1708 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [VT82xx]

Simple mixer control 'Master Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 27
  Mono: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 27
  Mono: Playback 22 [81%] [-8.75dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 21 [78%] [-10.50dB] [on]
  Front Right: Playback 21 [78%] [-10.50dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 20 [65%] [-5.25dB] [on]
  Front Right: Playback 20 [65%] [-5.25dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.50dB] [on]
  Front Right: Playback 25 [81%] [3.50dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-40.25dB] [off]
  Front Right: Playback 0 [0%] [-40.25dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Stereo Mixer'


!!Alsactl output
!!-------------

--startcollapse--
state.VT82xx {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Master Front Playback Volume'
		value.0 23
		value.1 23
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 27'
		iface MIXER
		name 'Front Playback Volume'
		value.0 27
		value.1 27
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 27'
		iface MIXER
		name 'Surround Playback Volume'
		value.0 27
		value.1 27
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 27'
		iface MIXER
		name 'Center Playback Volume'
		value 27
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 27'
		iface MIXER
		name 'LFE Playback Volume'
		value 22
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 27'
		iface MIXER
		name 'Side Playback Volume'
		value.0 21
		value.1 21
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Side Playback Switch'
		value.0 true
		value.1 true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 27'
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 27
		value.1 27
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 23
		value.1 23
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 true
		value.1 true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Line Playback Volume'
		value.0 20
		value.1 20
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
		name 'CD Playback Volume'
		value.0 25
		value.1 25
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
		comment.range '0 - 20'
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 20'
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.27 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Stereo Mixer'
		comment.item.1 Mic
		comment.item.2 'Front Mic'
		comment.item.3 Line
		comment.item.4 CD
		iface MIXER
		name 'Input Source'
		value 'Stereo Mixer'
	}
	control.28 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.29 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.30 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0282000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.32 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
	}
	control.33 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.34 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ipv6
af_packet
via
drm
acpi_cpufreq
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
cpufreq_ondemand
cpufreq_conservative
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
ac
snd_via82xx
gameport
snd_ac97_codec
ac97_bus
snd_mpu401_uart
sbp2
parport_pc
lp
parport
snd_hda_intel
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_page_alloc
snd_hwdep
snd_seq_dummy
evdev
snd_seq_oss
snd_seq_midi
psmouse
snd_rawmidi
snd_seq_midi_event
serio_raw
snd_seq
snd_timer
snd_seq_device
snd
soundcore
pcspkr
button
i2c_viapro
i2c_core
shpchp
pci_hotplug
via_agp
agpgart
reiserfs
usbhid
hid
sg
sr_mod
cdrom
sd_mod
pata_via
ohci1394
ieee1394
via_rhine
mii
ata_generic
ehci_hcd
uhci_hcd
pata_acpi
usbcore
libata
scsi_mod
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
fuse

```

---

### Post by kingu on 2008-04-18
It now has sound, so it seems that somewhere along an update something went wrong. It was fixed by installing the beta 4 again and then updating. 

However this have spawned a new problem. When watching a DVD riped to the machines harddrive only stereo sound is produced. Can anyone explain that, and help to solve it?

It seems that i pulse audio is bypassed by letting VLC use the alsa plugin, 5.1 sound is played.

---

