---
title: "Karmic 5.1 sound choppy, stereo works fine."
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dr_dred5 on 2009-09-27
I've just installed 9.10 and everything is working much better than anticipated with this one exception.

The audio works fine in analogue stereo mode, but when I switch to analogue 5.1 the sound almost completely cuts out with intermittent choppy bursts, about two per second. The sound however does come out of all six speakers.

I've been using Ubuntu since 6.06 and am used to having to set things up for 5.1. In the past I've opened the mixer and turned of digital output, edited **/etc/pulse/daemon.conf** and change the speaker line to “**Set default-sample-channels = 6**”

With Karmic, the mixer is missing and editing daemon.conf hasn't worked.

I've done a lot of searching and haven't found a bug report that relates to this specific problem, so I'm assuming that I'm doing something wrong. I'm assuming it's something to do with Pulseaudio, but I am not sure how to change the setup.

Hopefully someone can point me in the right direction.

Here's my relevant info.

Ubuntu 9.10 x86 alpha 6 all updates installed.
Soundcard: Soundblaster 5.1 Live
Pentium 4 2.4gh
Logitek 5.1 analogue speakers.

I've configured the hardware by right clicking on the audio icon in the system tray. Under hardware, the only device listed is “Internal Audio 1 Output” and I have selected Analogue surround 5.1 output.

Alsamixer lists the following:

```
Card: SB Live! 5.1                                                           &#9474;

&#9474; Chip: SigmaTel STAC9708,11                                                   &#9474;

&#9474; View: [Playback] Capture  All                                                &#9474;

&#9474; Item: Surround [dB gain=-16.40, -16.40]

```
Which looks normal to me. I've also played with all the sliders and have made sure that nothing is muted.

I've tried audio from VLC, Movie Player, Banshee and Rythembox. All required codecs have been installed.

Output of aplay -l
```

**** List of PLAYBACK Hardware Devices ****

card 0: Live [SB Live! 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]

  Subdevices: 32/32

  Subdevice #0: subdevice #0

  Subdevice #1: subdevice #1

  Subdevice #2: subdevice #2

  Subdevice #3: subdevice #3

  Subdevice #4: subdevice #4

  Subdevice #5: subdevice #5

  Subdevice #6: subdevice #6

  Subdevice #7: subdevice #7

  Subdevice #8: subdevice #8

  Subdevice #9: subdevice #9

  Subdevice #10: subdevice #10

  Subdevice #11: subdevice #11

  Subdevice #12: subdevice #12

  Subdevice #13: subdevice #13

  Subdevice #14: subdevice #14

  Subdevice #15: subdevice #15

  Subdevice #16: subdevice #16

  Subdevice #17: subdevice #17

  Subdevice #18: subdevice #18

  Subdevice #19: subdevice #19

  Subdevice #20: subdevice #20

  Subdevice #21: subdevice #21

  Subdevice #22: subdevice #22

  Subdevice #23: subdevice #23

  Subdevice #24: subdevice #24

  Subdevice #25: subdevice #25

  Subdevice #26: subdevice #26

  Subdevice #27: subdevice #27

  Subdevice #28: subdevice #28

  Subdevice #29: subdevice #29

  Subdevice #30: subdevice #30

  Subdevice #31: subdevice #31

card 0: Live [SB Live! 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]

  Subdevices: 8/8

  Subdevice #0: subdevice #0

  Subdevice #1: subdevice #1

  Subdevice #2: subdevice #2

  Subdevice #3: subdevice #3

  Subdevice #4: subdevice #4

  Subdevice #5: subdevice #5

  Subdevice #6: subdevice #6

  Subdevice #7: subdevice #7

card 0: Live [SB Live! 5.1], device 3: emu10k1 [Multichannel Playback]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

```

Any pointers would be greatly appreciated.

Cheers!

---

### Post by overdrank on 2009-09-27
Moved to Karmic Koala Testing and Discussion

---

### Post by Headsick on 2009-09-30
I have the same problem, but a little bit different.
Karmic detects my sound card (Audigy4) as an "Audigy2 Value".
So only possibility to get sound is setting the output module to "Digital Stereo (IEC958 )" (S/PDIF); this is two-channel-stereo and not "Analog 5.1 Surround" sound I had before. My amplifier is connected to 5 Plugs on my sound card and not to the S/PDIF-Connector.
Playing with alsamixer or the daemon.conf has no effect.

Any ideas to solve the wrong driver problem and let me hear the good old 5.1-Sound?


Thanks for help,

Lg Headsick

---

### Post by dr_dred5 on 2009-10-01
In previous distros, in the sound preferences, you could change the drivers, IE Pulse, Alsa, Sigmatel.

Is there any way to do this in Karmic? Alsamixer displays the correct card, but in Sound Preferences, my card is only listed as "Internal Audio" and there is no information on what what driver is being used.

Is there any way to check and alter these settings?

Cheers!

---

### Post by gnomeuser on 2009-10-01
ubuntu-bug pulseaudio - this should work, as it does not it is a bug and tracking it at least would be helpful. 5.1 should just work out of the box, yet it rarely does.

---

### Post by dr_dred5 on 2009-10-02
I figured I'd wait a few days before making a bug report. Actually I figured there would already be one and here it is.

Bug number 440921 and it can be tracked at [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/440921](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/440921)

Cheers.

---

### Post by markbuntu on 2009-10-02
Is there surround sound listings in Sound Preferences/hardware?
If not then it is more likely a alsa driver or udev problem than a pulseaudio issue.
Did you run system test?
if you did and saved it there is way more than all the info you need about your hardware and software.

---

### Post by dr_dred5 on 2009-10-03
> **markbuntu said:**
> Is there surround sound listings in Sound Preferences/hardware?
If not then it is more likely a alsa driver or udev problem than a pulseaudio issue.
Did you run system test?
if you did and saved it there is way more than all the info you need about your hardware and software.

Hi Mark.

Yes, surround sound is listed in the hardware settings and when selected I do get sound out of all 6 speakers, but it's garbled.

What other system tests should I run? The only ones I know of are the ones listed in post #1. I'm willing to run any tests you want. 

As a last resort, I'm willing to try to build Pulse/Alsa from source if needed, but looking at their Wiki's, it looks like a pretty big job.

Thanks for the suggestions.

---

### Post by markbuntu on 2009-10-03
Check in /etc/pulse/daemon.conf and try uncommenting the line
enable-remixing=yes

You can also try changing the default sample rate from 44100 to 48000, some cards are only capable of 48000. 

You can also try changing the default-fragments and increasing the default-fragment-size but that is usally necessary only if the sound is suttering.

You can read about these settings by typing in a terminal

man pulse-daemon.conf

---

### Post by sandyd on 2009-10-03
just completely remove pulseaudio
```

sudo apt-get remove pulseaudio*

```

---

### Post by Yes_It's_Me on 2009-10-04
Yeah, that's the sad reality. :(

It sucks too, a few months ago when i installed karmic I thought they were so damn close. But there is just so many damn problems. Pulseaudio and however they implement it on ubuntu is just rubbish.

---

### Post by dr_dred5 on 2009-10-04
> **markbuntu said:**
> Check in /etc/pulse/daemon.conf and try uncommenting the line
enable-remixing=yes

You can also try changing the default sample rate from 44100 to 48000, some cards are only capable of 48000. 

You can also try changing the default-fragments and increasing the default-fragment-size but that is usally necessary only if the sound is suttering.

You can read about these settings by typing in a terminal

man pulse-daemon.conf

Thanks for the sugestions Mark. I tried it with no luck. 

I'm going to spend some time reading up on Pulse today to see if I can come up with any other ideas.

---

### Post by briancb on 2009-10-15
Hi

I was wondering why karmic had no digital 5.1 listed but I chose digital stereo duplex and ran a 5.1 movie in VLC Player and my sound system recognized it and played no problem.

---

### Post by dr_dred5 on 2009-10-17
Looks like there's a duplicate of the bug that's also been confirmed, assigned and given high importance.

```
https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/445849
```

---

### Post by ales on 2009-10-17
Hmmm, I just installed the 9.10 and stereo works by default. In pulse audio preferences I have to manualy select 5.1 output always for every playback, then it works. Otherwise it's always only stereo

---

### Post by ales on 2009-10-17
Hello,

i have installed the 9.10 today and after cahnging something in daemon.conf the 5.1 sound works.

What I did u can see in the attached file. I have SB Live 5.1 and I had to manually always set stereo and then back to 5.1 output in the pulseaudio prefernces to get 5.1 sound.
I enabled in daemon. conf item "module loading - yes" and it works now automatically. I also changed oyher thoing but that have no influecne on sound. 
Still there is something like steel noice in the sound.


Ales

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
**[COLOR="black"]allow-module-loading = yes[/COLOR]**
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
enable-remixing = yes
enable-lfe-remixing = yes

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

default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 6
; default-channel-map = front-left,front-right, rear-left, rear-right, center

default-fragments = 8
default-fragment-size-msec = 10

---

