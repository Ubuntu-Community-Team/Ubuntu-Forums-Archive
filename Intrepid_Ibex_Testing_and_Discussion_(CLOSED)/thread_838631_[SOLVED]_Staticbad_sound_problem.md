---
title: "[SOLVED] Static/bad sound problem"
date: 2008-06-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by KIAaze on 2008-06-23
I'm having some sound problems currently.
I hear the sound with static over it.

Here's what I get when testing sound in the sound preferences dialog:
pcsp -> not OK
ALI 5451 -> OK
ALSA -> OK
ESD -> not OK
OSS -> OK
PulseAudio -> not OK

After setting all things to ALSA or OSS instead of automatic detection, music and videos play correctly with Totem, but ONLY with totem.
With all other players, I hear the sound with static over it. The same happens with Youtube/flash videos.

More info:

```
$lspci -v | grep -i audio
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)

```

```
$pulseaudio --version
pulseaudio 0.9.10

```

```
$uname -a
Linux my-laptop 2.6.26-1-generic #1 SMP Fri Jun 13 13:22:43 UTC 2008 i686 GNU/Linux

```

```
$dpkg -l | grep alsa
ii  alsa-base                                  1.0.16-1.1ubuntu3                                  ALSA driver configuration files
ii  alsa-oss                                   1.0.15-1                                           ALSA wrapper for OSS applications
ii  alsa-utils                                 1.0.16-1ubuntu1                                    ALSA utilities
ii  alsaplayer-esd                             0.99.80-2ubuntu1                                   PCM player designed for ALSA (EsounD output 
ii  gstreamer0.10-alsa                         0.10.20-1                                          GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.38-0ubuntu9                                    Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-1.10.10-plugins-alsa                 1.10.10-1ubuntu6                                   Portable Windows Library Audio Plugin for th
ii  libsdl1.2debian-alsa                       1.2.13-2ubuntu1                                    Simple DirectMedia Layer (with X11 and ALSA 
ii  xfce4-mixer-alsa                           1:4.4.2-3ubuntu1                                   Xfce4 Mixer ALSA backend

```

---

### Post by mc4100 on 2008-06-23
I had a similar problem - System=>Preferences=>Sound had no effect, only OSS could produce sound. No issue with static, though.
It might not work for you, but try:
Alt+F2, "pavucontrol", and moving the current app's sound, you do this through the tiny little arrow on the right. The settings seem to stay once set, but changing the default in "Output Devices" tab reverts back after a reboot.
Again, this is only what works for me, so no guarantees.

---

### Post by soccerboy on 2008-06-23
[http://ubuntuforums.org/showthread.php?t=833825](http://ubuntuforums.org/showthread.php?t=833825) discusses solutions to a similar problem.  See if it fixes your problem.

---

### Post by KIAaze on 2008-06-23
> **mc4100 said:**
> I had a similar problem - System=>Preferences=>Sound had no effect, only OSS could produce sound. No issue with static, though.
It might not work for you, but try:
Alt+F2, "pavucontrol", and moving the current app's sound, you do this through the tiny little arrow on the right. The settings seem to stay once set, but changing the default in "Output Devices" tab reverts back after a reboot.
Again, this is only what works for me, so no guarantees.

Thanks, that worked. :)
I'll still have a look at soccerboy's link to see if there's a better solution.

edit: Sound working even after reboot. :)
I used this solution: [http://ubuntuforums.org/showpost.php?p=5216747&postcount=3](http://ubuntuforums.org/showpost.php?p=5216747&postcount=3)
Didn't have to blacklist the PC speaker as suggested elsewhere.

---

### Post by soccerboy on 2008-06-25
> **KIAaze said:**
> Thanks, that worked. :)
I'll still have a look at soccerboy's link to see if there's a better solution.

edit: Sound working even after reboot. :)
I used this solution: [http://ubuntuforums.org/showpost.php?p=5216747&postcount=3](http://ubuntuforums.org/showpost.php?p=5216747&postcount=3)
Didn't have to blacklist the PC speaker as suggested elsewhere.

glad it worked.

---

