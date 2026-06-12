---
title: "No sound after upgrade to 9.10   AMD 64"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xigen on 2009-10-08
Hello,

My sound is no longer working after an upgrade (9.04 -> 9.10).  AMD64

I have a delta66 card and the motherboard has an audio output. I believe all is set to work with the delta66 card.



$ speaker-test -Dplug:surround51 -c6 -l1 -twav

gave me a nice sound output & speaker test


wilson@wilson-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M66 [M Audio Delta 66], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


wilson@wilson-desktop:~$ lspci -v
01:07.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
	Subsystem: VIA Technologies Inc. Device d632
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at b800 [size=32]
	I/O ports at b400 [size=16]
	I/O ports at b000 [size=16]
	I/O ports at ac00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ICE1712
	Kernel modules: snd-ice1712

wilson@wilson-desktop:~$ grep 'audio' /etc/group
audio:x:29:pulse

Any suggestions?

:guitar:

---

### Post by xigen on 2009-10-08
Here is the output from 
wilson@wilson-desktop:~$ wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh

(* it was a little long -- so I posed the URL)

[http://www.alsa-project.org/db/?f=1fa104dd672c3682957282be98f143fc0348d282](http://www.alsa-project.org/db/?f=1fa104dd672c3682957282be98f143fc0348d282)

---

### Post by daetsy on 2009-10-08
I have experienced the same loss of sound. It seems that the the sound is muted. The solution was to install gnome alsamixer and un mute all the outputs. It might work for you

---

### Post by xigen on 2009-10-08
Here is a screenshot of my alsamixer-gui

Is there something muted?  

Cheers.

---

### Post by xigen on 2009-10-08
for good measure -- here is a screenshot of alsamixer.

---

### Post by xigen on 2009-10-08
my gnome-alsamixer screenshot

... so... do you see anything which needs to be un-muted?

Cheers.

also -- here is the output of 
wilson@wilson-desktop:~$ gnome-alsamixer

** (gnome-alsamixer:2820): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958"!

** (gnome-alsamixer:2820): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958"!

** (gnome-alsamixer:2820): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Deemphasis"!

** (gnome-alsamixer:2820): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Deemphasis"!

** (gnome-alsamixer:2820): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "H/W"!

** (gnome-alsamixer:2820): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "H/W"!

** (gnome-alsamixer:2820): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "H/W"!

** (gnome-alsamixer:2820): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "H/W"!

** (gnome-alsamixer:2820): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Multi Track Internal Clock"!

** (gnome-alsamixer:2820): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Multi Track Internal Clock Default"!

---

### Post by daetsy on 2009-10-08
In the last screenshot all the sliders are at minimum. I don't know what those on the right are for, but they are all muted. If you use S/PDIF you should check the IEC958 boxes.

---

### Post by xigen on 2009-10-08
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

SoundTroubleshootingProcedure

results of: 
wget -O alsa-info.sh [http://212.20.107.51/alsa-info.sh](http://212.20.107.51/alsa-info.sh) 
bash alsa-info.sh --pastebin 

(here)   [http://pastebin.ca/1605557](http://pastebin.ca/1605557)

full bug report:
[https://bugs.launchpad.net/ubuntu/+bug/446813](https://bugs.launchpad.net/ubuntu/+bug/446813)

cheers.

---

### Post by xigen on 2009-10-08
hmmm... 

I changed the levels (see new screenshot)

and still no sound.

Let's see (*though I doubt it) if a reboot will make any difference.

---

### Post by xigen on 2009-10-09
I got a reply from launchpad.  Unfortunately I still do not have sound.


Simple mixer control 'ADC',0
 Capabilities: volume volume-joined
 Playback channels: Mono
 Capture channels: Mono
 Limits: 0 - 163
 Mono: 0 [0%] [-99999.99dB]
Simple mixer control 'ADC',1
 Capabilities: volume volume-joined
 Playback channels: Mono
 Capture channels: Mono
 Limits: 0 - 163
 Mono: 0 [0%] [-99999.99dB]
Simple mixer control 'ADC',2
 Capabilities: volume volume-joined
 Playback channels: Mono
 Capture channels: Mono
 Limits: 0 - 163
 Mono: 0 [0%] [-99999.99dB]
Simple mixer control 'ADC',3
 Capabilities: volume volume-joined
 Playback channels: Mono
 Capture channels: Mono
 Limits: 0 - 163
 Mono: 0 [0%] [-99999.99dB]

Your ADC volume is at 0%. Please increase it to 77%


And this issue:

Simple mixer control 'DAC',2
 Capabilities: volume volume-joined
 Playback channels: Mono
 Capture channels: Mono
 Limits: 0 - 127
 Mono: 0 [0%] [-99999.99dB]
Simple mixer control 'DAC',3
 Capabilities: volume volume-joined
 Playback channels: Mono
 Capture channels: Mono
 Limits: 0 - 127
 Mono: 0 [0%] [-99999.99dB]

Your DAC volume is at 0%. Please increase it to 77%


In envy24control , alsamixer and gnome-alsamixer,  you need to make sure that the ADC and DAC volume channels are set to 77% of maximum volume and that you don't have any of the channels muted in the mixer. Also go to the
command line and type in alsamixer and check that your levels are turned up there as well.

In gnome-alsamixer, you might need to click on "preferences" to be able
to view any extra hidden volume channels. Maybe the DAC and ADC volume
channels are hidden from view in your gnome-alsamixer panel.
...............

---

### Post by xigen on 2009-10-09
Proposed answer:

Looks like there are still more channels with volume set to 0%, like the
Multi Track Peak channel:

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

................

Still - no sound.

when I boot up -- there is no sound.
when I run the command: speaker-test -Dplug:surround51 -c6 -l1 -twav
it sounds beautiful

when I upgraded to 9.04 ... I had issues with hardware.  Specifically Ubuntu needed to distinguish between onboard sound and my delta66 soundcard.   I wonder if that is a factor in my current issue.

I went through
-- alsamixer
-- gnome-alsamixer
-- envy24control
and I turned up the settings on all 'multi'  ** see screenshots

---

### Post by xigen on 2009-10-09
envy24control screenshots

---

### Post by xigen on 2009-10-09
( suggestion from launchpad)

Run this command in a terminal:

gksudo gedit /etc/pulse/daemon.conf

# Replace the following line in /etc/pulse/daemon.conf

; default-sample-channels = 2

# with the following line:

default-sample-channels = 6

Then save the change to /etc/pulse/daemon.conf

Then reboot and retest sound.


_____________________________________

gksudo gedit /etc/pulse/daemon.conf ... done.
reboot ... done

Still, no sound.   

...

wilson@wilson-desktop:~$ cat /etc/pulse/daemon.conf
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 6
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

....

Suggestions?

---

### Post by xigen on 2009-10-10
My instructions were not followed correctly: there is a ; in front of
the line

default-sample-channels = 6

The ; character means that the line is commented out and not active!

So OR you remove the ; in front that line or you add the following line
to /etc/pulse/daemon.conf

default-sample-channels = 6

Then reboot and retest sound. If that does not help, then I think you
are experiencing this annoying bug in pulseaudio:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

...............

( I think I got it right this time) 

reboot ... check

Sound ... still .. No Sound.  

............

wilson@wilson-desktop:~$ cat /etc/pulse/daemon.conf
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
  default-sample-channels = 6
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

---

### Post by groening on 2009-10-26
I've been there...
Took me hours to get it working, plz try the following:

1) Open PulseAudio's new Volumebar go to preferences and set the hardware to 5.1 Sound (don't mix up analog/digital!)

2) open a terminal and execute: ```
aplay -L
```
you should get an output with the name of your card and some outputs
```
front:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
```
3) now test the following from a terminal (in my case the right one was surround51): ```
speaker-test -c6 -Dplug:surround51
```

you should see a numbered list of channels (repeatingly but that doesn't bother us r8 now..)
```
speaker-test 1.0.20

Das Wiedergabegerät ist plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Samplingrate auf 48000Hz gesetzt (gefordert waren 48000Hz)
Buffer size range from 64 to 5440
Period size range from 32 to 2720
Using max buffer size 5440
Periods = 4
was set period_size = 1088
was set buffer_size = 5440
 0 - Vorne Links
 4 - Center
 1 - Vorne Rechts
 3 - Hinten Rechts
 2 - Hinten Links
 5 - Low Frequency Effects (Subwoofer)
Time per period = 8,546960
```

4) open up /etc/pulse/daemon.conf and enter your channels manually:
(Be sure not to mix up the numerations from the channels! in my case lfe is BEHIND center)
```
...
default-sample-channels = 6
default-channel-map = front-left,front-right,rear-left,rear-right,center,lfe
...
```

4) close the file and execute ```
pulseaudio -k
```
(pulseaudio should restart itself)

5) open alsamixer in a terminal and increase volumes

That should do the job - now you can tune the channels as you like...

EDIT: after a restart I was able to change the volumes from pulseaudios volumebar ;-)

hope it helps...

---

