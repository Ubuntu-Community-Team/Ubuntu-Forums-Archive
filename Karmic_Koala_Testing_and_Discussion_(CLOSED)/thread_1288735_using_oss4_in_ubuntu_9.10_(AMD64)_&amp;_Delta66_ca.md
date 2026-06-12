---
title: "using oss4 in ubuntu 9.10 (AMD64) &amp; Delta66 card"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xigen on 2009-10-11
I am having a lot of trouble using PulseAudio
... see
[http://ubuntuforums.org/showthread.php?t=1286047](http://ubuntuforums.org/showthread.php?t=1286047)
also 
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

I am attempting to install oss4 ... as per
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
(* see bottom)

...

Oss4 is installed and I am still not getting sound

Suggestions?

...
Details:

wilson@wilson-desktop:~/Desktop$ sudo dpkg -i oss-linux-4.2-2000_amd64.deb 
[sudo] password for wilson: 
(Reading database ... 251692 files and directories currently installed.)
Preparing to replace oss-linux 4.2-2000 (using oss-linux-4.2-2000_amd64.deb) ...
 * Shutting down ALSA...                                                 [ OK ] 
Unpacking replacement oss-linux ...
Upgrading OSS - will not purge /usr/lib/oss.
Setting up oss-linux (4.2-2000) ...
Building OSS Modules for Linux-unknown 2.6.31-12-generic

OSS build environment set up for REGPARM kernels

Building module osscore
Building module lynxone
Building module lynxtwo
Building module oss_ali5455
Building module oss_atiaudio
Building module oss_audigyls
Building module oss_audioloop
Building module oss_audiopci
Building module oss_cmi878x
Building module oss_cmpci
Building module oss_cs4281
Building module oss_cs461x
Building module oss_digi96
Building module oss_emu10k1x
Building module oss_envy24
Building module oss_envy24ht
Building module oss_fmedia
Building module oss_geode
Building module oss_hdaudio
Building module oss_hdsp
Building module oss_ich
Building module oss_imux
Building module oss_madi
Building module oss_midiloop
Building module oss_midimix
Building module oss_sblive
Building module oss_sbpci
Building module oss_sbxfi
Building module oss_solo
Building module oss_trident
Building module oss_usb
Building module oss_userdev
Building module oss_via823x
Building module oss_via97
Building module oss_ymf7xx
depmod -a
Forcing re-detection of installed soundcards
Starting Open Sound System

************************************************************
* NOTE! You are using trial version of Open Sound System   *
************************************************************


Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
wilson@wilson-desktop:~/Desktop$ sudo apt-get install -y gstreamer0.10-plugins-bad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-bad is already the newest version.
The following packages were automatically installed and are no longer required:
  rtkit libgconfmm-2.6-1c2 paman pavumeter
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
wilson@wilson-desktop:~/Desktop$ 

$ osstest works perfectly and sounds terrific
$ ossmix see output below
$ ossinfo -v3 see output below

Also -- When I go to
System --> Preferences --> Sound
I get: "Waiting for sound system to respond"


.....
wilson@wilson-desktop:~/Desktop$ ossmix
Selected mixer 0/M Audio Delta 66
Known controls are:
mon.out1/2 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.out3/4 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.spdout [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.in1/2 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.in3/4 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.spdin [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
route.out1/2 <DMA|MONITOR|IN1/2|IN3/4|SPDIF> (currently DMA)
route.out3/4 <DMA|IN1/2|IN3/4|SPDIF> (currently DMA)
route.spdif <DMA|MONITOR|IN1/2|IN3/4|SPDIF> (currently DMA)
gain.out1/2 <+4DB|CONSUMER|-10DB> (currently +4DB)
gain.out3/4 <+4DB|CONSUMER|-10DB> (currently +4DB)
gain.in1/2 <+4DB|CONSUMER|-10DB> (currently +4DB)
gain.in3/4 <+4DB|CONSUMER|-10DB> (currently +4DB)
envy24.rate <8000|9600|11025|12000|16000|22050|24000|32000|44100|48000|88200|96000> (currently 48000)
envy24.sync <INTERNAL|SPDIF> (currently INTERNAL)
envy24.ratelock ON|OFF (currently ON)
envy24.actrate <decimal value> (currently 48000) (Read-only)
wilson@wilson-desktop:~/Desktop$ ossinfo -v3
Version info: OSS 4.2 (b 2000/200909100609) (0x00040100) TRIAL
Platform: Linux/x86_64 2.6.31-12-generic #41-Ubuntu SMP Wed Oct 7 19:37:12 UTC 2009 (wilson-desktop)

Number of audio devices: 9
Number of audio engines: 9
Number of MIDI devices: 0
Number of mixer devices: 1


Device objects
0: osscore0 OSS core services
1: oss_envy240 M Audio Delta 66 interrupts=15 (15)
2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
0: M Audio Delta 66 (Mixer 0 of device object 1)
Device file /dev/oss/oss_envy240/mix0, Legacy device /dev/mixer0
Priority: 0
Caps:
Device handle: PCId6321412-0000:01:07.0-mx01
Device priority: 0


Audio devices
M Audio Delta 66 out1/2 /dev/oss/oss_envy240/pcm0 (device index 0)
Legacy device /dev/dsp0
Caps: TRIGGER
Modes: OUTPUT
Out engine 1: 0/M Audio Delta 66 out1/2
Available for use
Input formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Output formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Device handle: PCId6321412-0000:01:07.0-au01
Related mixer dev: 0
Sample rate source: 0
Preferred channel configuration: STEREO
Supported number of channels (min - max): 1 - 10
Native sample rates (min - max): 8000 - 96000 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
HW Type: Not indicated.
Minimum latency: Not indicated

M Audio Delta 66 out3/4 /dev/oss/oss_envy240/pcm1 (device index 1)
Legacy device /dev/dsp1
Caps: TRIGGER
Modes: OUTPUT
Out engine 1: 1/M Audio Delta 66 out3/4
Available for use
Input formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Output formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Device handle: PCId6321412-0000:01:07.0-au02
Related mixer dev: 0
Sample rate source: 0
Preferred channel configuration: STEREO
Supported number of channels (min - max): 1 - 8
Native sample rates (min - max): 8000 - 96000 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
HW Type: Not indicated.
Minimum latency: Not indicated

M Audio Delta 66 S/PDIF out /dev/oss/oss_envy240/spdout (device index 2)
Legacy device /dev/dsp2
Caps: TRIGGER
Modes: OUTPUT
Out engine 1: 2/M Audio Delta 66 S/PDIF out
Available for use
Input formats (0x00009410):
AFMT_S16_LE - 16 bit signed little endian
AFMT_AC3 - AC3 (Dolby Digital) encoded audio
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Output formats (0x00009410):
AFMT_S16_LE - 16 bit signed little endian
AFMT_AC3 - AC3 (Dolby Digital) encoded audio
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Device handle: PCId6321412-0000:01:07.0-au03
Related mixer dev: 0
Sample rate source: 0
Preferred channel configuration: STEREO
Supported number of channels (min - max): 1 - 2
Native sample rates (min - max): 8000 - 96000 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
HW Type: DIGITAL_OUT Minimum latency: Not indicated

M Audio Delta 66 in1/2 /dev/oss/oss_envy240/pcmin0 (device index 3)
Legacy device /dev/dsp3
Caps: TRIGGER
Modes: INPUT
In engine 1: 3/M Audio Delta 66 in1/2
Available for use
Input formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Output formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Device handle: PCId6321412-0000:01:07.0-au04
Related mixer dev: 0
Sample rate source: 0
Preferred channel configuration: STEREO
Supported number of channels (min - max): 1 - 12
Native sample rates (min - max): 8000 - 44100 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
HW Type: Not indicated.
Minimum latency: Not indicated

M Audio Delta 66 in3/4 /dev/oss/oss_envy240/pcmin1 (device index 4)
Legacy device /dev/dsp4
Caps: TRIGGER
Modes: INPUT
In engine 1: 4/M Audio Delta 66 in3/4
Available for use
Input formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Output formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Device handle: PCId6321412-0000:01:07.0-au05
Related mixer dev: 0
Sample rate source: 0
Preferred channel configuration: STEREO
Supported number of channels (min - max): 1 - 10
Native sample rates (min - max): 8000 - 44100 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
HW Type: Not indicated.
Minimum latency: Not indicated

M Audio Delta 66 S/PDIF in /dev/oss/oss_envy240/spdin (device index 5)
Legacy device /dev/dsp5
Caps: TRIGGER
Modes: INPUT
In engine 1: 5/M Audio Delta 66 S/PDIF in
Available for use
Input formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Output formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Device handle: PCId6321412-0000:01:07.0-au06
Related mixer dev: 0
Sample rate source: 0
Preferred channel configuration: STEREO
Supported number of channels (min - max): 1 - 4
Native sample rates (min - max): 8000 - 44100 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
HW Type: Not indicated.
Minimum latency: Not indicated

M Audio Delta 66 input from mon. mixer /dev/oss/oss_envy240/mon (device index 6)
Legacy device /dev/dsp6
Caps: TRIGGER
Modes: INPUT
In engine 1: 6/M Audio Delta 66 input from mon. mixer
Available for use
Input formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Output formats (0x00009010):
AFMT_S16_LE - 16 bit signed little endian
AFMT_S32_LE - 32 bit signed little endian
AFMT_S24_LE - 24/32 bit signed little endian
Device handle: PCId6321412-0000:01:07.0-au07
Related mixer dev: 0
Sample rate source: 0
Preferred channel configuration: STEREO
Supported number of channels (min - max): 1 - 2
Native sample rates (min - max): 8000 - 44100 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
HW Type: Not indicated.
Minimum latency: Not indicated

M Audio Delta 66 (all outputs) /dev/oss/oss_envy240/10ch_out (device index 7)
Legacy device /dev/dsp7
Caps: TRIGGER MMAP
Modes: OUTPUT
Out engine 1: 7/M Audio Delta 66 (all outputs)
Available for use
Input formats (0x00001000):
AFMT_S32_LE - 32 bit signed little endian
Output formats (0x00001000):
AFMT_S32_LE - 32 bit signed little endian
Device handle: PCId6321412-0000:01:07.0-au08
Related mixer dev: 0
Sample rate source: 0
Preferred channel configuration: MULTICH
Supported number of channels (min - max): 10 - 10
Native sample rates (min - max): 8000 - 96000
HW Type: Not indicated.
Minimum latency: Not indicated

M Audio Delta 66 (all inputs) /dev/oss/oss_envy240/12ch_in (device index 8)
Legacy device /dev/dsp8
Caps: TRIGGER MMAP
Modes: INPUT
In engine 1: 8/M Audio Delta 66 (all inputs)
Available for use
Input formats (0x00001000):
AFMT_S32_LE - 32 bit signed little endian
Output formats (0x00001000):
AFMT_S32_LE - 32 bit signed little endian
Device handle: PCId6321412-0000:01:07.0-au09
Related mixer dev: 0
Sample rate source: 0
Preferred channel configuration: MULTICH
Supported number of channels (min - max): 12 - 12
Native sample rates (min - max): 8000 - 96000
HW Type: Not indicated.
Minimum latency: Not indicated


Nodes
/dev/dsp -> /dev/oss/oss_envy240/pcm0
/dev/dsp_in -> /dev/oss/oss_envy240/pcmin0
/dev/dsp_out -> /dev/oss/oss_envy240/pcm0
/dev/dsp_ac3 -> /dev/oss/oss_envy240/spdout
/dev/dsp_multich -> /dev/oss/oss_envy240/pcm0
/dev/dsp_spdifout -> /dev/oss/oss_envy240/spdout

---

### Post by xigen on 2009-10-11
My attempt to fix the issue based on:
[www.4front-tech.com/forum/viewtopic.php?f=3&t=3324#p13408](www.4front-tech.com/forum/viewtopic.php?f=3&t=3324#p13408)

VLC ... works
Totem 2.28.1 .. does not work
Amarok 2.x ... does not work and sends me into a KDE config screen (below) where the choice I want (M-Audio Delta 66) appears and yet cannot be selected.

...

wilson@wilson-desktop:~$ gst-inspect-0.10 | grep OSS
oss4:  oss4mixer: OSS v4 Audio Mixer
oss4:  oss4src: OSS v4 Audio Source
oss4:  oss4sink: OSS v4 Audio Sink
ossaudio:  osssink: Audio Sink (OSS)
ossaudio:  osssrc: Audio Source (OSS)
ossaudio:  ossmixer: OSS Mixer
wilson@wilson-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
wilson@wilson-desktop:~$ 
wilson@wilson-desktop:~$ gconf-editor

---

### Post by xigen on 2009-10-12
[http://www.4front-tech.com/forum/viewtopic.php?f=3&t=3324#p13408](http://www.4front-tech.com/forum/viewtopic.php?f=3&t=3324#p13408)
(toward the bottom)

xine

    * Write the following line to ~/.xine/config

          audio.driver:oss 

xmms2

    * Install the OSS output plugin
          o Ubuntu Intrepid: apt-get install xmms2-plugin-oss 
    * Modify the output plugin in the config file
          o Replace alsa with oss in the output plugin configuration entry inside the xmms config file (which should be ~/.config/xmms2/xmms2.conf) 

.....


wilson@wilson-desktop:~$ !503
cat ~/.config/xmms2/xmms2.conf
cat: /home/wilson/.config/xmms2/xmms2.conf: No such file or directory

...

I do not see the file 
~/.config/xmms2/xmms2.conf

suggestions?

---

### Post by Yellow Pasque on 2009-10-12
See my response to your thread on the OSS4 forum.

---

### Post by LKjell on 2009-10-12
> **Temüjin said:**
> See my response to your thread on the OSS4 forum.

Any chance for a link for those curious in mind?

---

### Post by Yellow Pasque on 2009-10-12
> **LKjell said:**
> Any chance for a link for those curious in mind?
[http://www.4front-tech.com/forum/viewtopic.php?f=3&t=3352](http://www.4front-tech.com/forum/viewtopic.php?f=3&t=3352)

---

### Post by xigen on 2009-10-12
About Flash: Sorry, I forgot that I built the 32-bit version myself and that you won't have it (I also forgot to tell you to run ldconfig). So:

Code: Select all
    sudo rm /usr/lib32/libflashsupport.so
    cd ~/
    wget [http://www.fileupyours.com/view/77985/libflashsupport.so](http://www.fileupyours.com/view/77985/libflashsupport.so)
    sudo chown root:root libflashsupport.so
    sudo chmod 644 libflashsupport.so
    sudo mv libflashsupport.so
    sudo ldconfig


Now try again :P

About the gstreamer test: Did you have any other app using sound at the time? If you run 'ossxmix' is vmix available?

...

Here is what $ ossxmix 
produces..

---

### Post by xigen on 2009-10-13
sound in flash ... works... just not well.

It sounds very scratchy/fragmented/broken.

...

I am running an AMD64 system.  
sudo mv libflashsupport.so /usr/lib32/

is this the correct library for an AMD64 system?

---

