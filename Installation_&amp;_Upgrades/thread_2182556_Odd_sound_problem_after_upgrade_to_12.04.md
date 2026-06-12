---
title: "Odd sound problem after upgrade to 12.04"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by Keith_Beef on 2013-10-21
After an upgrade to 12.04, I have a nasty clicking noise coming out of the Vaio speakers.

When I look in the sound config I see that the output is constantly switching between the built-in speakers and the headphone socket and back again. I've not seen this problem before, not on this hardware or on any other (Linux since 1997, in my household, and on this Vaio since 2008 or 2009). 

Any ideas?

---

### Post by Keith_Beef on 2013-10-22
Nobody?

I started poking around, and found a config file for Pulseaudio.

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

; Path for mixers that have a 'Speaker' control
;
; See analog-output.conf.common for an explanation on the directives

[General]
priority = 100
name = analog-output-speaker

; This is a workaround (would be better to be able to disable automute everywhere)
[Jack Headphone]
state.plugged = no
state.unplugged = unknown

[Jack Front Headphone]
state.plugged = no
state.unplugged = unknown

[Jack Speaker Phantom]
required-any = any
state.plugged = unknown
state.unplugged = unknown

[Element Hardware Master]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element Master]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element Master Front]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = front-left,front-right

[Element Master Mono]
switch = off
volume = off

; This profile path is intended to control the speaker, not the
; headphones. But it should not hurt if we leave the headphone jack
; enabled nonetheless.
[Element Headphone]
switch = mute
volume = zero

[Element Headphone2]
switch = mute
volume = zero

[Element Speaker]
required-any = any
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element Desktop Speaker]
switch = off
volume = off

[Element Front]
switch = mute
volume = merge
override-map.1 = all-front
override-map.2 = front-left,front-right

[Element Front Speaker]
switch = mute
volume = merge
override-map.1 = all-front
override-map.2 = front-left,front-right
required-any = any

[Element Rear]
switch = mute
volume = merge
override-map.1 = all-rear
override-map.2 = rear-left,rear-right

[Element Surround]
switch = mute
volume = merge
override-map.1 = all-rear
override-map.2 = rear-left,rear-right

[Element Surround Speaker]
switch = mute
volume = merge
override-map.1 = all-rear
override-map.2 = rear-left,rear-right
required-any = any

[Element Side]
switch = mute
volume = merge
override-map.1 = all-side
override-map.2 = side-left,side-right

[Element Center]
switch = mute
volume = merge
override-map.1 = all-center
override-map.2 = all-center,all-center

[Element Center Speaker]
switch = mute
volume = merge
override-map.1 = all-center
override-map.2 = all-center,all-center
required-any = any

[Element LFE]
switch = mute
volume = merge
override-map.1 = lfe
override-map.2 = lfe,lfe

[Element LFE Speaker]
switch = mute
volume = merge
override-map.1 = lfe
override-map.2 = lfe,lfe
required-any = any

.include analog-output.conf.common
```

---

### Post by Keith_Beef on 2013-10-24
Bump…

I've been looking around, but still haven't found any explanation of how to understand the various config files for PulseAudio.

```
$ ls -al /usr/share/pulseaudio/alsa-mixer/paths/*.conf
-rw-r--r-- 1 root root 1470 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-aux.conf
-rw-r--r-- 1 root root 1861 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input.conf
-rw-r--r-- 1 root root 2146 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-dock-mic.conf
-rw-r--r-- 1 root root 1475 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-fm.conf
-rw-r--r-- 1 root root 2156 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-front-mic.conf
-rw-r--r-- 1 root root 2353 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-headphone-mic.conf
-rw-r--r-- 1 root root 2243 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-headset-mic.conf
-rw-r--r-- 1 root root 2853 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-internal-mic-always.conf
-rw-r--r-- 1 root root 3231 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-internal-mic.conf
-rw-r--r-- 1 root root 2350 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-linein.conf
-rw-r--r-- 1 root root 2494 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic.conf
-rw-r--r-- 1 root root 1512 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic-line.conf
-rw-r--r-- 1 root root 2146 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-rear-mic.conf
-rw-r--r-- 1 root root 1480 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-tvtuner.conf
-rw-r--r-- 1 root root 1451 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-input-video.conf
-rw-r--r-- 1 root root 2402 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf
-rw-r--r-- 1 root root 2313 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-output-desktop-speaker.conf
-rw-r--r-- 1 root root 2108 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones-2.conf
-rw-r--r-- 1 root root 2377 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf
-rw-r--r-- 1 root root 1991 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-output-lfe-on-mono.conf
-rw-r--r-- 1 root root 1949 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-output-mono.conf
-rw-r--r-- 1 root root 2909 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-output-speaker-always.conf
-rw-r--r-- 1 root root 3261 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/analog-output-speaker.conf
-rw-r--r-- 1 root root   97 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/hdmi-output-0.conf
-rw-r--r-- 1 root root   99 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/hdmi-output-1.conf
-rw-r--r-- 1 root root   99 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/hdmi-output-2.conf
-rw-r--r-- 1 root root   99 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/hdmi-output-3.conf
-rw-r--r-- 1 root root  778 Sep 26 11:13 /usr/share/pulseaudio/alsa-mixer/paths/iec958-stereo-output.conf
```

---

### Post by Keith_Beef on 2013-11-30
Looks like this question interests nobody&#8230;

I now think that the crackling is due to a hardware problem. The 1/3" (3.5mm) earphone jack socket is under the panel at the bottom right of the keyboard, where my right hand rests sometimes while typing. I think that the weight of my hand must have damaged the wiring inside, causing the computer to falsely detect a jack plug being inserted and removed. For now, the solution is to plug in a jack connected to nothing, and use a DAC on a USB port for sound output.

I would like to know if there is some way in software to defeat the detection, and leave the built-in speakers and also the headphone socket switched off; so I'm not marking this as solved, yet.

---

### Post by germanix on 2013-11-30
I cannot help you solve this problem but let me offer you this bit of information:
I have a Sony Viao and when Ubuntu 12.04 first came out I Installed it on my Sony with no problems. Then later I deleted it and installed Xubuntu. Two weeks ago I again installed Ubuntu 12.04 and experienced the same problem you now have. This drove me crazy. I thought it must be a hardware problem and that my trusted Sony is breaking up. So to test it I deleted 12.04 again and re-installed Xubuntu, and the problem was gone. This let me to believe that this was a software problem that must have happened with later updates to Ubuntu 12.04, I also tried 12.10 which had the same problem. So I would suggest try another distro first to see if the problem disappears before you give the hardware the fault.

---

### Post by Keith_Beef on 2013-12-05
> **germanix said:**
> I have a Sony Viao and when Ubuntu 12.04 first came out I Installed it on my Sony with no problems. Then later I deleted it and installed Xubuntu. Two weeks ago I again installed Ubuntu 12.04 and experienced the same problem you now have. This drove me crazy. I thought it must be a hardware problem and that my trusted Sony is breaking up. So to test it I deleted 12.04 again and re-installed Xubuntu, and the problem was gone. This let me to believe that this was a software problem that must have happened with later updates to Ubuntu 12.04, I also tried 12.10 which had the same problem. So I would suggest try another distro first to see if the problem disappears before you give the hardware the fault.

That's very interesting, and certainly worth trying. I don't really want to wipe out and re-install what I already have, so I'll look at booting a live distribution from a CD or DVD first.

---

