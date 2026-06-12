---
title: "no sound Hp DV2000 Kubuntu plz help"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by forum2forum on 2007-11-30
Hi have installed kubuntu and no sound on m HP dv 2000 series have followed this links but nogo
 
 [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
 
 have checked the codec used for my laptop using cat /proc/asound/card0/codec\#*
 it says
 
 Codec: Conexant CX20549 (Venice)
 Address: 0
 Vendor Id: 0x14f15045
 Subsystem Id: 0x103c30b5
 Revision Id: 0x100100
 Default PCM:
 rates [0x140]: 48000 96000
 bits [0xe]: 16 20 24
 formats [0x1]: PCM
 Default Amp-In caps: N/A
 Default Amp-Out caps: N/A
 Node 0x10 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
 Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
 Amp-Out vals: [0x2b 0x2b]
 Pincap 0x0810014: OUT EAPD Detect
 Pin Default 0x95170110: [Fixed] Speaker at Int Top
 Conn = Analog, Color = Unknown
 Pin-ctls: 0x40: OUT
 Power: 0x0
 Connection: 2
 0x19 0x17*
 Node 0x11 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
 Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
 Amp-Out vals: [0x2b 0x2b]
 Pincap 0x08113c: IN OUT HP Detect
 Pin Default 0x0221401f: [Jack] HP Out at Ext Front
 Conn = 1/8, Color = Green
 Pin-ctls: 0xc0: OUT HP
 Power: 0x0
 Connection: 2
 0x19 0x17*
 Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
 Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
 Amp-Out vals: [0x14 0x14]
 Pincap 0x08113c: IN OUT HP Detect
 Pin Default 0x22a1902e: [Jack] Mic at Sep Front
 Conn = 1/8, Color = Pink
 Pin-ctls: 0x20: IN
 Power: 0x0
 Connection: 2
 0x19 0x17*
 Node 0x13 [Pin Complex] wcaps 0x400301: Stereo Digital
 Pincap 0x0810: OUT
 Pin Default 0x01447130: [Jack] SPDIF Out at Ext Rear
 Conn = RCA, Color = Yellow
 Pin-ctls: 0x00:
 Connection: 1
 0x18
 Node 0x14 [Pin Complex] wcaps 0x400081: Stereo
 Pincap 0x081124: IN Detect
 Pin Default 0x97a70120: [Fixed] Mic at Int Riser
 Conn = Analog, Color = Unknown
 Pin-ctls: 0x24: IN
 Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
 Pincap 0x0820: IN
 Pin Default 0x94330121: [Fixed] CD at Int Right
 Conn = ATAPI, Color = Unknown
 Pin-ctls: 0x00:
 Node 0x16 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
 Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0b, mute=1
 Amp-Out vals: [0x06]
 Node 0x17 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
 Amp-In caps: ofs=0x14, nsteps=0x2b, stepsize=0x05, mute=1
 Amp-In vals: [0x94 0x94] [0x94 0x94] [0x94 0x94] [0x94 0x94] [0x94 0x94]
 Power: 0x0
 Connection: 5
 0x19 0x14 0x12 0x11 0x15
 Node 0x18 [Audio Output] wcaps 0x211: Stereo Digital
 PCM:
 rates [0x40]: 48000
 bits [0x6]: 16 20
 formats [0x5]: PCM AC3
 Node 0x19 [Audio Output] wcaps 0xc11: Stereo
 PCM:
 rates [0x540]: 48000 96000 192000
 bits [0xe]: 16 20 24
 formats [0x1]: PCM
 Power: 0x0
 Node 0x1a [Audio Input] wcaps 0x100d0b: Stereo Amp-In
 Amp-In caps: ofs=0x00, nsteps=0x17, stepsize=0x05, mute=1
 Amp-In vals: [0x17 0x17] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
 Power: 0x0
 Connection: 5
 0x17 0x14* 0x12 0x11 0x15
 Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono
 
 
 
 
 please help me out.

---

### Post by ReKast on 2007-12-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Had the same problem with Ubuntu on HP 2660se, this is what i did:

looking [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246") i found the following:
cyril damas posts:
"last news... if we compare difference between generic and i386 kernel, we can see that package modules for kernel 2.22.14 is not installed. but installed with generic kernel who it works well...
so i installed linux-ubuntu-modules-2.6.22-14-386 and sound is back with default gutsy kernel 2.6.22-14-i386!!"

went to synaptic and installed linux-ubuntu-modules-2.6.22-14-386, however
doing that knocked out my restricted drivers (built in wireless card), so going to the restricted drivers option i was prompted to install linux-restricted-modules-2.6.22-14-386.
I updated the reqested files, restarted, and heard the intro sound, I'm not sure how you would do this in kubuntu, but i figure just find the equivilant drivers, Hope this helps!

---

### Post by spiderbatdad on 2008-02-13
ack!

---

