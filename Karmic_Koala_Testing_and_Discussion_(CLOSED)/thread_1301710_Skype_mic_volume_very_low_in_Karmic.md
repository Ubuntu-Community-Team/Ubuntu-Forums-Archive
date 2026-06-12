---
title: "Skype mic volume very low in Karmic"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cipicip on 2009-10-26
Hi guys,

Just finished installing Ubuntu 9.10 amd64 on my machine, installed skype and... the mic volume is very, very low. Totally useless.

What I tried so far:
 - purged pulseaudio
 - set all levels on max in the gnome UI
 - maxed out all levels in alsamixer
 - set skype voice settings on intel hd:0 something (instead of default)
 - unchecked "Let Skype set the volume" option

And right now I'm running out of options. Previously I had kubuntu 9.10 and the volume was fine. I would have stayed with that except the dual screen mode is broken (the cloned screen bug).

I've posted this question also on the skype forums: 
[http://forum.skype.com/index.php?showtopic=455671](http://forum.skype.com/index.php?showtopic=455671)

Any suggestions?

Thanks.

EDIT: added the link to the skype forum thread.

---

### Post by nikgare on 2009-10-26
I had the same problem on 9.10 amd64 - it turned out my mic was turned almost right down in Sound Prefences - have you looked in there?

---

### Post by cipicip on 2009-10-26
> **nikgare said:**
> I had the same problem on 9.10 amd64 - it turned out my mic was turned almost right down in Sound Prefences - have you looked in there?

I did. Everything is set to max. Except in the sound pref it says "unamplified" even though the amplifiers are set to max too. :S

---

### Post by mbradlcu on 2009-10-26
> **cipicip said:**
> I did. Everything is set to max. Except in the sound pref it says "unamplified" even though the amplifiers are set to max too. :S

check the mixer preferences, you may need to enable another capture source. Also check out 'alsamixer' it may have more variables available.

---

### Post by cipicip on 2009-10-26
> **mbradlcu said:**
> check the mixer preferences, you may need to enable another capture source. Also check out 'alsamixer' it may have more variables available.

In alsamixer there are 3 capture sources: 2 digital mic (which in linux never worked), and an analogue one. All 3 are enabled and all 3 have their volume set to max and all 3 have the amplifiers enabled and set to max. As for the sound pref, everthing on the input section is enabled and set to max.

The sound does work, except it's very, very low.

---

### Post by mbradlcu on 2009-10-26
> **cipicip said:**
> In alsamixer there are 3 capture sources: 2 digital mic (which in linux never worked), and an analogue one. All 3 are enabled and all 3 have their volume set to max and all 3 have the amplifiers enabled and set to max. As for the sound pref, everthing on the input section is enabled and set to max.

The sound does work, except it's very, very low.

oops didn't actually mean capture, more like output or pre out. Have you checked out 'amixer scontents' . reason I bring this up again is that the new mixer only shows all mixer simple controls,, on my system there's a lot more the what's shown.

---

### Post by cipicip on 2009-10-26
> **mbradlcu said:**
> oops didn't actually mean capture, more like output or pre out. Have you checked out 'amixer scontents' . reason I bring this up again is that the new mixer only shows all mixer simple controls,, on my system there's a lot more the what's shown.

Unfortunately everything is at 100% and still nothing. Bellow is the output :S

```

$ amixer scontents
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',1
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'Digital Playback' 'ADAT' 'Analog Mux 1' 'Analog Mux 2' 'Analog Mux 3'
  Item0: 'Digital Playback'
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%] [21.00dB] [on]
  Front Right: Capture 14 [100%] [21.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%] [21.00dB] [off]
  Front Right: Capture 14 [100%] [21.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%] [21.00dB] [off]
  Front Right: Capture 14 [100%] [21.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Digital Input Source',0
  Capabilities: enum
  Items: 'Analog Inputs' 'Digital Mic 1'
  Item0: 'Digital Mic 1'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%] [40.00dB]
  Front Right: Capture 4 [100%] [40.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%] [40.00dB]
  Front Right: Capture 4 [100%] [40.00dB]
Simple mixer control 'Mux',2
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%] [40.00dB]
  Front Right: Capture 4 [100%] [40.00dB]
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [off]

```

---

### Post by Westmeath on 2009-10-26
Which version of Skype are you running?

Skype 2.1 beta is in the Medibuntu repository. It uses pulseaudio. Much better sound quality.

After installing I usually have to go into Sound Preferences > Input tab & set Input Volume to about half.

I have often had trouble getting the old version of Skype working.

---

### Post by cipicip on 2009-10-26
> **Westmeath said:**
> Which version of Skype are you running?

Skype 2.1 beta is in the Medibuntu repository. It uses pulseaudio. Much better sound quality.

After installing I usually have to go into Sound Preferences > Input tab & set Input Volume to about half.

I have often had trouble getting the old version of Skype working.

Version 2.0. I'll try version 2.1 and see how it goes.

---

### Post by cipicip on 2009-10-26
> **cipicip said:**
> Version 2.0. I'll try version 2.1 and see how it goes.

YES! Finally! It works. Version 2.1 with pulse. Selected "Analog Stereo Duplex" for hardware profile in the mixer.

---

