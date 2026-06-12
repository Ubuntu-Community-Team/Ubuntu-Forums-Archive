---
title: "PulseAudio Wont Start After Upgrade From 19.10 to 20.04"
date: 2020-04-10
forum: Installation &amp; Upgrades
---

### Post by rjnicholson1591 on 2020-04-10
I updated my system from Kubuntu 19.10 to 20.04, after updating I have no sound at all.
Running pulseaudio form the terminal fails with this error:
```
W: [pulseaudio] pid.c: Stale PID file, overwriting
W: [pulseaudio] alsa-ucm.c: UCM file does not specify 'PlaybackChannels' or 'CaptureChannels'for device Mic1, assuming stereo duplex.
W: [pulseaudio] alsa-ucm.c: UCM file does not specify 'PlaybackChannels' or 'CaptureChannels'for device Mic2, assuming stereo duplex.
W: [pulseaudio] alsa-ucm.c: UCM file does not specify 'PlaybackChannels' or 'CaptureChannels'for device Line2, assuming stereo duplex.
W: [pulseaudio] alsa-ucm.c: UCM file does not specify 'PlaybackChannels' or 'CaptureChannels'for device Headphones, assuming stereo duplex.
W: [pulseaudio] alsa-ucm.c: UCM file does not specify 'PlaybackChannels' or 'CaptureChannels'for device Line1, assuming stereo duplex.
W: [pulseaudio] alsa-ucm.c: UCM file does not specify 'PlaybackChannels' or 'CaptureChannels'for device Speaker, assuming stereo duplex.
E: [pulseaudio] alsa-ucm.c: Assertion 'jack' failed at modules/alsa/alsa-ucm.c:2158, function device_add_hw_mute_jack(). Aborting.
fish: “pulseaudio” terminated by signal SIGABRT (Abort)
```

---

### Post by CelticWarrior on 2020-04-10
Does it work in a 20.04 live session? If so, do your backups (you should have those already) and install from scratch. It's that simple.

---

### Post by rjnicholson1591 on 2020-04-10
> **CelticWarrior said:**
> Does it work in a 20.04 live session? If so, do your backups (you should have those already) and install from scratch. It's that simple.
I'm hoping to avoid reinstalling from scratch due to having over 500GB of games on my main partition and an awful download speed to recover those.

---

### Post by CelticWarrior on 2020-04-10
I also have lots of games but almost all managed via Steam and in a separated partition. I never have to reinstall them.

---

### Post by rjnicholson1591 on 2020-04-10
> **CelticWarrior said:**
> I also have lots of games but almost all managed via Steam and in a separated partition. I never have to reinstall them.
Yeah I've recently moved my main rig over to windows so only have the one ssd, I've decided to format another ssd over to ext4, thankfully I have the luxury of extra drives so can backup a few games but I'd rather fix the problem if possible than sidestep it by nuking the system, I've got another PC on 19.10 but now I'm scared to upgrade that one to 20.04 in case I get the same issue again.

---

### Post by CelticWarrior on 2020-04-10
FYI, 20.04 hasn't been released yet.

---

### Post by rjnicholson1591 on 2020-04-10
> **CelticWarrior said:**
> FYI, 20.04 hasn't been released yet.
True, my bad in jumping over to it early, I figured it'll be out in only a few days so would be fairly stable.

---

### Post by mörgæs on 2020-04-11
It would probably have been stable in a clean install.

---

