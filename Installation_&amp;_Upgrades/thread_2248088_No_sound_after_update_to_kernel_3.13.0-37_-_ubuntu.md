---
title: "No sound after update to kernel 3.13.0-37 - ubuntu 14.04 x64"
date: 2014-10-12
forum: Installation &amp; Upgrades
---

### Post by manco1911 on 2014-10-12
Hi guys, its beeb a while. 
OK, here is the thing, i upgraded a couple of days ago to the latest kernel:

```
uname -a
Linux tirith 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Hadn't use the box much, but today i realized i have no sound.
```

I tried reinstalling alsa, alsa-utils, alsa-base, pulseaudio completly with no results. Alsamixer recognizes fine my sound hardware but no luck on making it work.

```
lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel     HDA) (rev 40)
    Subsystem: ASUSTeK Computer Inc. M5A88-V EVO
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe8f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
```

Here is my alsa-info.sh output: [http://www.alsa-project.org/db/?f=ca02a907243342a21346fbd1f07118b28ab395c5](http://www.alsa-project.org/db/?f=ca02a907243342a21346fbd1f07118b28ab395c5)

I also tried booting to the last "sound working" kernel 3.13.0-36 but no luck either. I really don't know what else to try here...

Any help will be much appreciated.

[UPDATE]
I installed pavucontrol and i can "see" VLC and Rythmbox sound playing.. but still no sound. Output hardware is correctly selected by default, no muted. 
Alsamixer also displays all volumes up, non muted. I even disabled "<Auto-Mute>" just in case. 

Please, its been more than 24hs, i'd really love to get my audio back

---

### Post by sankaman82 on 2014-10-13
Hi,

just got the same issue after updating to kernel 3.13.0-37, on the same way.
alsa-info.sh output: [http://www.alsa-project.org/db/?f=b60402fcc1fd0527abc520f98f5ff64319b41580](http://www.alsa-project.org/db/?f=b60402fcc1fd0527abc520f98f5ff64319b41580)

Thanks for any feedback.

uname -a:
Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014 i686 i686 i686 GNU/Linux

---

### Post by Scary Rob on 2014-10-13
Last time I updated anything was a couple of days ago. Mid-session, an hour or two ago, my sound just vanished without trace. Bringing up the alsa controls, there are no volume sliders, just a little box where they should be with 00 in it and <S/PDIF> immediately underneath that. 

Linux Bedevere 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014 i686 athlon i686 GNU/Linux

---

### Post by sankaman82 on 2014-10-14
Ok,
without any reason,
This morning, after a laptop's sleepmode, it's working back.
I'm sorry for the mail above and also for the ? concerning the solution...

---

### Post by Scary Rob on 2014-10-15
More information

Because I had to install PulseAudio manually in 12.04 so Skype would work, I wondered if installing PulseAudio would do anything. Apparently it was already installed, so I tried uninstalling it instead. Result: I lost my volume control graphic on the panel and still had no sound. So I reinstalled PulseAudio and installed Pavucontrol, wondering if it could give me access to a setting that I didn't know had changed.

With Pavucontrol open, and while playing a youtube video, I am still getting no sound, but ALSA Plug-in box under the 'playback' tab is showing activity: the blue indicator bar showing signal levels is twitching nicely but I'm still getting no actual sound. I've tried changing speakers - it's definitely not them failing.

Any thoughts, anybody?

---

### Post by Scary Rob on 2014-10-22
Just an update - I've submitted a bug report, as we seem to be out of ideas.

---

