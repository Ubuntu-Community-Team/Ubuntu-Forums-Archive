---
title: "Warzone 2100 Broken Audio"
date: 2008-12-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-12-10
Is anyone else replicating broken audio on warzone 2100?

If you havent tried this game, its quite a good little real time strategy game in 3d.

Anyway I get scrambled, noisy, poppy audio. Other OpenAL seems ok.

Thanks

---

### Post by Nullack on 2008-12-11
If you dont have it, why not "test" it? Could be fun :)

---

### Post by ronacc on 2008-12-12
I'm not a gamer but since no one else was answering you I d/l'd it and yes scratchy crackling noise here too .

---

### Post by plun on 2008-12-12
Ok... Within Jauntys repo...!  I got some sort of sound after following Arch wiki

> **Configuration of OpenAL for PulseAudio**

Games that uses OpenAL can use PulseAudio directly writing this line in ~/**.openalrc**:

(define devices '(esd))

or alternatively

(define devices '(alsa))
(define alsa-device "pulse")


[http://wiki.archlinux.org/index.php/PulseAudio](http://wiki.archlinux.org/index.php/PulseAudio)


I can also see the stream now with **[pavucontrol]("http://packages.ubuntu.com/jaunty/pavucontrol")** .... but sounds a little strange
(running game in windowed mode)

Howto play is another challenge....):P

---

### Post by caryb on 2008-12-12
I decided to install this out of curiosity (& the bosses bandwidth) not being a gamer too it fired up & made clean sounds:p test 2 17 year-old daughter & 3 hours later, I got what a awesome game dad! great graphics & sound! Can I have it on my PC please? She has Kubuntu Hardy)



I guess it works here:lolflag:

Cary

---

### Post by Nullack on 2008-12-27
Well I tried the workaround from the arch wiki:

nullack@PPP:~$ cat ~/.openalrc
(define devices '(alsa))
(define alsa-device "pulse")
nullack@PPP:~$ 

And that does not fix the sound being corrupted.

EDIT: I just tried Glest which I understand uses OpenAL and that also has wrecked audio. What can I do in regard to configuration items to see what might fix it?

EDIT: Also this doesnt work:

nullack@PPP:~$ cat .openalrc 
(define devices '(esd))
nullack@PPP:~$

---

### Post by plun on 2008-12-27
Well... I have sound, but running PulseAudio from GIT.

Can you see the stream with pavucontrol ?

Also closing everything and kill PA for more clues

```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

Then run the game in **Windowed mode** and check **pavucontrol** and the **terminal window** for clues.

:)

---

### Post by Nullack on 2008-12-27
Yes I see it in pavucontrol - that is once I installed padevchooser.

Anyway in the terminal log I get this:

D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 64568 bytes on render memblockq.
D: protocol-native.c: Requesting rewind due to end of underrun.
D: module-alsa-sink.c: Requested to rewind 65536 bytes.
D: module-alsa-sink.c: Limited to 168 bytes.
D: module-alsa-sink.c: before: 42
D: module-alsa-sink.c: after: 42
D: module-alsa-sink.c: Rewound 168 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 168 bytes on render memblockq.
I: module-alsa-sink.c: Underrun!
D: protocol-native.c: Requesting rewind due to end of underrun.
D: module-alsa-sink.c: Requested to rewind 5504 bytes.
D: module-alsa-sink.c: Limited to 308 bytes.
D: module-alsa-sink.c: before: 77
D: module-alsa-sink.c: after: 77
D: module-alsa-sink.c: Rewound 308 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 308 bytes on render memblockq.
I: module-alsa-sink.c: Underrun!
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 becomes idle.
D: module-alsa-sink.c: hwbuf_unused_frames=0
D: module-alsa-sink.c: setting avail_min=65185
D: module-alsa-sink.c: Requested to rewind 65536 bytes.
D: module-alsa-sink.c: Limited to 204 bytes.
D: module-alsa-sink.c: before: 51
D: module-alsa-sink.c: after: 51
D: module-alsa-sink.c: Rewound 204 bytes.
D: sink.c: Processing rewind...
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing input 242 "ALSA Playback"
I: module-stream-restore.c: Restoring device for stream sink-input-by-application-name:ALSA plug-in [warzone2100].
I: module-stream-restore.c: Restoring volume for sink input sink-input-by-application-name:ALSA plug-in [warzone2100].
D: module-stream-restore.c: Not restoring mute state for sink input sink-input-by-application-name:ALSA plug-in [warzone2100], because already set.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 becomes busy.
D: memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: sink-input.c: Created input 243 "ALSA Playback" on alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: protocol-native.c: Requested tlength=185.76 ms, minreq=0.72 ms
D: protocol-native.c: Early requests mode enabled, configuring sink latency to minreq.
D: memblockq.c: memblockq requested: maxlength=4194304, tlength=32768, base=4, prebuf=32640, minreq=128 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=4194304, tlength=32768, base=4, prebuf=32640, minreq=128 maxrewind=0
I: protocol-native.c: Final latency 186.48 ms = 184.31 ms + 2*0.72 ms + 0.72 ms
D: module-alsa-sink.c: latency set to 4.00ms
D: module-alsa-sink.c: hwbuf_unused_frames=16208
D: module-alsa-sink.c: setting avail_min=16561
D: module-alsa-sink.c: Requesting rewind due to latency change.
D: module-alsa-sink.c: Requested to rewind 65536 bytes.
D: module-alsa-sink.c: Limited to 64444 bytes.

Underruns and rewinds. Any ideas folks? Im going to do a bug report.

---

### Post by Nullack on 2008-12-27
Its [bug 311853]("https://bugs.launchpad.net/bugs/311853") so can someone please confirm the bug.

---

### Post by marmuta on 2008-12-28
Added to the bug and confirmed it. 
libao-pulse has been deleted from Jaunty though. libao and/or pulseaudio might be better matches.

For a workaround, does just killing pulseaudio help?
I haven't tested with Warzone but this cured openal with my apps. Openal via pure alsa seems to work fine.

```

pulseaudio -k
mplayer -ao openal /usr/lib/openoffice/share/gallery/sounds/space2.wav 

```

---

### Post by Nullack on 2008-12-31
Thanks alot marmuta :)

Not only did you confirm the status but you also provided a workaround - legendary.

---

