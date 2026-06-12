---
title: "Sound problems after 14.04 upgrade in Myth"
date: 2015-06-06
forum: Installation &amp; Upgrades
---

### Post by Blue_Screen on 2015-06-06
Greetings,

I have just upgraded to 14.04.  Now the sound has failed in Myth TV, It appears functional for everything except Myth.  The sound is sent through an HDMI connection to TV.  
I have searched and followed the recommendations of several postings on this forum and other sites.  Here is what I have so far:

In Myth TV when starting a DVD or live TV in a notification box it states "Disabling auto audio Player Aborting Reconfigure"
I then ran "mythfrontend -v"  and noticed these errors
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM dmix:CARD=NVidia,DEV=7
14:01:54.282895 I  Pulse: PulseAudio suspend OK
14:01:54.287992 E  ALSA: snd_pcm_open("dmix:CARD=NVidia,DEV=7"): No such file or directory
14:01:54.288252 N  AudioPlayer: Enabling Audio

I attempted to go to Setup\Audio with this result -

ALSA lib control.c:953:(snd_ctl_open_noupdate) Invalid CTL hw:0
Handling Segmentation fault
Segmentation fault (core dumped)

And mythfrontend crashes.

aplay -l gives the following result

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -lL ends with this result

a52:CARD=NVidia
    HDA NVidia
a52:CARD=CX23885
    Conexant CX23885
**** List of PLAYBACK Hardware Devices ****
ALSA lib control.c:953:(snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:277: control open (0): No such file or directory
ALSA lib control.c:953:(snd_ctl_open_noupdate) Invalid CTL hw:1
aplay: device_list:277: control open (1): No such file or directory
ALSA lib control.c:953:(snd_ctl_open_noupdate) Invalid CTL hw:2
aplay: device_list:277: control open (2): No such file or directory
*** Error in `aplay': munmap_chunk(): invalid pointer: 0x0000000001c2b290 ***
Aborted (core dumped)


I have followed the instructions here 
[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

and now the capture card is not working in MythTV

This error appears on the screen at login (I am not sure if it related but it started at the time of upgrade)
[   22.436571] Firmware and/or mailbox pointer not initialized or corrupted, signature = 0xfeffffff, cmd = PING_FW

The capture card is a Hauppauge HV1800 
lspci -v

Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 0f)
    Subsystem: Hauppauge computer works Inc. Device 7801
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fba00000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: cx23885

I am have hit a point where I do not know what else to check.  
I have Linux Mint 17 on the same computer and Myth runs with audio but the capture card although it does appear will not let me scan for channels.  I only mention this if there is a config file I can copy from that partition or a setting that I can reference in helping to get Myth working properly here.

Thank you for any thoughts or observations.

---

