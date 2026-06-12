---
title: "Crackling Audio"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-09-14
Gday folks

So is anyone else getting crackling audio? I have an audigy 2 sound card.

Anyone got a workaround until the existing set of bugs is fixed?

---

### Post by Nullack on 2009-09-19
This is ongoing for me. Theres bug reports so not much I can do there. Anyone got any workarounds?

---

### Post by dext on 2009-09-19
dunno but file bug reports about it

---

### Post by Nullack on 2009-09-20
bugs were subscribed too long ago :)

---

### Post by jmmL on 2009-09-20
Have you checked the sliders in alsamixer? I had crackling audio because the PCM level was set too high by default. To solve it, I lowered PCM and increased master.

---

### Post by Nullack on 2009-09-22
Ive had to bring the front slider in alsamixer down by a whole -24DB. This isnt right to need to modify this stuff out of the box.

---

### Post by psyke83 on 2009-09-22
> **Nullack said:**
> Gday folks

So is anyone else getting crackling audio? I have an audigy 2 sound card.

Anyone got a workaround until the existing set of bugs is fixed?

Can you be a little more specific?

There's three possibilities:
1. Audio is stuttering due to bugs in your audio card's kernel module *- try the tsched=0 workaround.*
2. You're hearing popping each time the codec is turned on or off, related to powersaving.
3. Your audio card suffers from distortion when the PCM mixer is above ~75% *- [disable flat volume logic]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-August/009227.html").*

Regarding point 3: the latest PulseAudio release uses flat volume logic, your audio may have distortions at ALL volume levels due to the way the flat volume logic operates. Previously you could ensure that the PCM slider was below 75%, but it doesn't seem to work anymore.

---

### Post by Nullack on 2009-09-22
Hi Conn,

Well Ive come up with a workaround.

Using alsamixer I blanked out all sliders for outputs except the PCM Front and PCM LFE. The problem of crackling / popping goes away.

If I then do nothing else but raise the front slider (not PCM front) when I get above -24DB or so, the crackling starts again.

---

### Post by psyke83 on 2009-09-22
> **Nullack said:**
> Hi Conn,

Well Ive come up with a workaround.

Using alsamixer I blanked out all sliders for outputs except the PCM Front and PCM LFE. The problem of crackling / popping goes away.

If I then do nothing else but raise the front slider (not PCM front) when I get above -24DB or so, the crackling starts again.

Maybe if you can isolate the problematic mixer (by re-enabling the muted mixers one by one), it may be worth filing a bug and perhaps this issue will be fixed by default the next time. Maybe it's one of the microphone inputs, for example?

---

### Post by Nullack on 2009-09-22
Heres the conditions:

All else set to mute except for PCM Front and PCM LFE. This gives no crackling / popping.

If I keep that setup, and do nothing else except for raising Front, from -24.8 DB onwards I get crackling / popping coming through. When I put it to mute or lower than 024.8db the crackling / popping stops again.

I have an Audigy 2 card.

---

### Post by psyke83 on 2009-09-22
> **Nullack said:**
> Heres the conditions:

All else set to mute except for PCM Front and PCM LFE. This gives no crackling / popping.

If I keep that setup, and do nothing else except for raising Front, from -24.8 DB onwards I get crackling / popping coming through. When I put it to mute or lower than 024.8db the crackling / popping stops again.

I have an Audigy 2 card.

Did you try to disable the flat volume logic and see if it helps? The real fix would need to be applied to the kernel module, I think, so that distortion doesn't occur at higher volumes.

---

### Post by Nullack on 2009-09-24
Well I looked at /etc/pulse/daemon.conf and by default it has:

flat-volumes = no

Which to me means it is off?

---

### Post by Nullack on 2009-09-25
The other problem with Pulse, which has very poorly existed for numerous cycles now without the bug being fixed, is that when using some apps the audio simply doesnt work. It comes out stuttered and inaudible. When I look at the logs I see this:

Sep 25 13:13:47 PPP pulseaudio[1940]: ratelimit.c: 139 events suppressed

---

### Post by Nullack on 2009-09-25
Any ideas Con or anyone else?

---

### Post by psyke83 on 2009-09-25
> **Nullack said:**
> The other problem with Pulse, which has very poorly existed for numerous cycles now without the bug being fixed, is that when using some apps the audio simply doesnt work. It comes out stuttered and inaudible. When I look at the logs I see this:

Sep 25 13:13:47 PPP pulseaudio[1940]: ratelimit.c: 139 events suppressed

I think it means that glitch-free audio doesn't work correctly for your kernel driver. You should file a bug, and keep glitch-free disabled until it's resolved.

To disable glitch-free:

Edit /etc/pulse/default.pa, and change this line:
```
load-module module-hal-detect
```

To this:
```
load-module module-hal-detect tsched=0
```

---

### Post by mc4man on 2009-09-25
I have audigy2 and audigy2 Zs on 2 karmic installs, 1 with a run of the mill 2.1 speakers the zs with half decent 5.1 monsoon planers. The sound is excellent on both out of the box

The only adjustments needed were the default pcm and master levels were to high, am able to lower all to the 70 -74 range.

Tested on all audio types from plain mp3 thru  24 bit 96, 192k wma's, and flac's. 2 ch -> 6 ch.

Don't have that line in /etc/pulse/default.pa

---

### Post by Nullack on 2009-09-25
> **mc4man said:**
> I have audigy2 and audigy2 Zs....the sound is excellent on both out of the box

Mate its not really out of the box because youve had to implement a workaround to reduce the sliders. Thats not what we call "just works". Plus its ugly because it then incorrectly shows the volume not being 100% when it cant go any higher without crackling.

---

### Post by Nullack on 2009-09-26
> **psyke83 said:**
> I think it means that glitch-free audio doesn't work correctly for your kernel driver. You should file a bug, and keep glitch-free disabled until it's resolved.

To disable glitch-free:

Edit /etc/pulse/default.pa, and change this line:
```
load-module module-hal-detect
```

To this:
```
load-module module-hal-detect tsched=0
```

Thanks pyske83

Ill try that. This bug appears to be related to OpenAL audio with Pulse. I will do a bug on this specific issue with garbled audio under OpenAL apps like Warzone 2100.

The other bug about crackling / popping, there is existing bugs I've subscribed too, reported my scenario on and checked the effects me too flag. These bugs have gone on for numerous cycles and frankly I dont think there is enough weight behind Ubuntu type devs contributing upstream to Pulse. It seems in Ubuntu for Pulse that its mainly a case of the work being packaging and not really being in control of the code itself or in fixing upstream bug issues. Problems with pulse is probably the weakest element of trying to use Desktop Ubuntu for most users I would think.

---

### Post by Nullack on 2009-09-26
I just tried to edit that file psyke and that string is not found. Heres the file:

```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav
load-sample-dir-lazy /usr/share/sounds/ubuntu/stereo

.fail

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
load-module module-cork-music-on-phone

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

---

### Post by psyke83 on 2009-09-27
> **Nullack said:**
> I just tried to edit that file psyke and that string is not found. Heres the file:

Hmm. Since HAL is deprecated by udev, you probably want to add "tsched=0" to the end of the "load-module module-udev-detect" line.

---

### Post by Nullack on 2009-09-27
I tried this:

load-module module-udev-detect tsched=0

Rebooted, not fixed. Its still garbled and messed up.

---

### Post by Nullack on 2009-09-29
Anyone know if this is an upstream bug or is it due to something Ubuntu configures/pacthes?

That might help to getting it resolved by going upstream since Ubuntu sound bugs tend to sit idle in the bug system.

---

### Post by Nullack on 2009-09-30
Just to add, upstream has a new release being pulseaudio 0.9.19. Doesnt seem to be all that much but some fixes is good.

---

