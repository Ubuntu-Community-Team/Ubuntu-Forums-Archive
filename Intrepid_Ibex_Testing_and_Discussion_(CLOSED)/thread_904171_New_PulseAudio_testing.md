---
title: "New PulseAudio testing"
date: 2008-08-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-08-29
Dev Luke Yelavich posted in ubuntu-devel-list that he has PulseAudio 0.9.11 in his PPA available for testing---his post(s) follow:

Greetings all,
I have made PulseAudio 0.9.11 available in my PPA(1). This is a call for testing of pulseaudio 0.9.11. I know a lot of users would like intrepid to ship with 0.9.11, but since a fair amount of changes have occurred between 0.9.10 and 0.9.11, I would like to get sufficient testing performed by the community at large before trying to push it into intrepid. For best results, please use kernel 2.6.27, as it contains alsa 1.0.17, needed by PulseAudio 0.9.11.

The reason why this is only available now is due to the kernel, and subsequently alsa, being updated so late in the intrepid cycle, something which I hope to address for intrepid+1.

An assessment of whether pulseaudio 0.9.11 is ready will be made after a couple of weeks of testing. I am willing to make updates to the package in my PPA to attempt to address issues as users find them. If you find any issues, please file a bug against pulseaudio in launchpad.

Thanks

Luke
(1)[http://launchpad.net/~themuso/+archive]("http://launchpad.net/%7Ethemuso/+archive")
On Thu, Aug 28, 2008 at 04:02:21PM EST, Luke Yelavich wrote:
If you find any issues, please file a bug against pulseaudio in launchpad.

To clarify, filing bugs against the ubuntu package is fine, but please indicate that you are filing a bug about pulseaudio 0.9.11 from my PPA.

Thanks

Luke

---

### Post by SunnyRabbiera on 2008-08-29
to be honest pulse should have been kept in testing in the first place, its too experimental.

---

### Post by autocrosser on 2008-08-29
I'm just trying to help make things better--and I think that anything that "helps" pulse is a improvement ;)

I'll be the "first" one to give it a whirl :)

---

### Post by SunnyRabbiera on 2008-08-29
> **autocrosser said:**
> I'm just trying to help make things better--and I think that anything that "helps" pulse is a improvement ;)

I'll be the "first" one to give it a whirl :)

well dont get me wrong pulse has a lot of potential but its just too new to have as a standard.

---

### Post by autocrosser on 2008-08-29
Well--it's almost D/L'd & I'll see if it totally "arfs my sound--will report back in 'bout 15 mins....

---

### Post by Nullack on 2008-08-29
> **SunnyRabbiera said:**
> well dont get me wrong pulse has a lot of potential but its just too new to have as a standard.

So d/l it and it get testing to improve its quality :)

---

### Post by autocrosser on 2008-08-29
No differences noted at this time--Flash "seems" a bit smoother playback---getting late here--will do more checking tomorrow.....

---

### Post by Sophont on 2008-08-29
> **SunnyRabbiera said:**
> to be honest pulse should have been kept in testing in the first place, its too experimental.

I keep hearing people have problem with PA.

But for me it worked out-of-the-box since Hardy (I reinstalled with Hardy Alpha 4 and have upgraded since then).

And it worked better with more apps then before PA.

I wonder why the experience is so different.

Rhythmbox, Totem, Mumble, Skype, games with wine (well Eve on Wine doesn't have sound if another sound using app already is running - but I turned down sound in Eve anyway - shrug) and without - it's not like I'm not using sound all the time.

I have done nothing special to configre it. And some tips regarding .asoundrc and .libao that I read here recently made things worse - so I just restored them to default.

On the whole PA has been a clear improvement for me. Out-of-the (Hardy Alpha) Box.

---

### Post by amano on 2008-08-29
The PulseAudio in the PPA should offer the "glitch free" feature....

---

### Post by ronacc on 2008-08-29
d/l'd and installed 0.9.11 , all ok so far .

---

### Post by hexion on 2008-08-29
Alpha testing required inside an alpha testing environment.
Should we be called meta-bugtesters? :)

I'll give it a go when I have some time and post here the results.

---

### Post by psyke83 on 2008-08-29
This is already being discussed in [another thread]("http://ubuntuforums.org/showthread.php?t=866965").

To avoid duplication, testers should confirm [bug #262326]("https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/262326") with this new version of PulseAudio.

N.B. You must have the PulseAudio ALSA plugins enabled!```
$ sudo apt-get install libasound2-plugins
$ asoundconf set-pulseaudio
```

---

### Post by psyke83 on 2008-08-29
> **Sophont said:**
> I keep hearing people have problem with PA.

But for me it worked out-of-the-box since Hardy (I reinstalled with Hardy Alpha 4 and have upgraded since then).

And it worked better with more apps then before PA.

I wonder why the experience is so different.

Rhythmbox, Totem, Mumble, Skype, games with wine (well Eve on Wine doesn't have sound if another sound using app already is running - but I turned down sound in Eve anyway - shrug) and without - it's not like I'm not using sound all the time.

I have done nothing special to configre it. And some tips regarding .asoundrc and .libao that I read here recently made things worse - so I just restored them to default.

On the whole PA has been a clear improvement for me. Out-of-the (Hardy Alpha) Box.

It seems quite likely that you aren't suffering from problems because you are lucky enough to own a sound card which supports hardware mixing (most cards don't). You are not running PulseAudio correctly if you don't have the proper .asoundrc configuration. 

If you don't believe me, while an application is playing sound, open the PulseAudio Volume Control and see if Skype, WINE and most of your games list themselves as a client on the Playback tab (answer: they won't). If it's not listed on that playback tab, it's not using PulseAudio, full stop.

---

### Post by plun on 2008-08-29
> **psyke83 said:**
> 
N.B. You must have the PulseAudio ALSA plugins enabled!```
$ sudo apt-get install libasound2-plugins
$ asoundconf set-pulseaudio
```

I cannot understand why the plugins isn't within the meta package...??

I would also change it to...

```
sudo apt-get install libasound2-plugins padevchooser
```


**About padevshooser:**

[http://packages.ubuntu.com/intrepid/padevchooser](http://packages.ubuntu.com/intrepid/padevchooser)

paman   = PulseAudio Manager 
paprefs  =  PulseAudio Preferences 
pavucontrol =  PulseAudio Volume Control 
pavumeter   = PulseAudio Volume Meter 


:guitar:


(It would also be nice if Luke maybe took the time and comment your post within Ubuntus mailing list and maybe also took the time and visit UF...)

---

### Post by plun on 2008-08-29
> **psyke83 said:**
> 
To avoid duplication, testers should confirm [bug #262326]("https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/262326") with this new version of PulseAudio.


Confirmed and added a comment to the bug.

> plun@dunder:~$ mplayer /usr/share/example-content/ubuntu\ Sax.ogg -ao alsa
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /usr/share/example-content/ubuntu Sax.ogg.
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 160.0 kbit/11.34% (ratio: 20000->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
mplayer: pcm_pulse.c:278: pulse_write: Assertion `pcm->last_size >= (size * pcm->frame_size)' failed.


---

### Post by Sophont on 2008-08-30
> **psyke83 said:**
> It seems quite likely that you aren't suffering from problems because you are lucky enough to own a sound card which supports hardware mixing (most cards don't). You are not running PulseAudio correctly if you don't have the proper .asoundrc configuration. 

If you don't believe me, while an application is playing sound, open the PulseAudio Volume Control and see if Skype, WINE and most of your games list themselves as a client on the Playback tab (answer: they won't). If it's not listed on that playback tab, it's not using PulseAudio, full stop.

My sound card according to lspci:
> Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


Dunno if that supports hardware mixing.

---

### Post by autocrosser on 2008-08-30
Sorry 'bout that---I haven't gone to that thread in a couple of weeks, so didn't see the update---perhaps we should have the threads merged.

In any case--one difference I have is that my system sounds have stopped--I believe that this is just a side effect from the updates in sound pref--everyone else have a grayed out sounds tab? It also looks like there will be the ability to create sound sets soon.

> **psyke83 said:**
> This is already being discussed in [another thread]("http://ubuntuforums.org/showthread.php?t=866965").

To avoid duplication, testers should confirm [bug #262326]("https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/262326") with this new version of PulseAudio.

N.B. You must have the PulseAudio ALSA plugins enabled!```
$ sudo apt-get install libasound2-plugins
$ asoundconf set-pulseaudio
```

---

### Post by nightfrost on 2008-08-30
I need to follow this thread.
This is great news, I _really_ hope 0.9.11 ends up in intrepid, in a nice implementation. Right now, I have no possibility of testing the ppa, but will do so as soon as I get a chance.

---

### Post by psyke83 on 2008-08-31
Can everyone testing Luke's packages please confirm the buffer size tests in aplay? [Bug #262326]("https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/262326"), comment 6. Try to find the minimum buffer size that triggers an assertion failure.

---

### Post by nightfrost on 2008-09-17
Hm... I'm getting a lot of these:
```
D: protocol-native.c: Requesting rewind due to end of underrun.
D: module-alsa-sink.c: Requested to rewind 34992 bytes.
D: module-alsa-sink.c: Limited to 264 bytes.
D: module-alsa-sink.c: before: 66
D: module-alsa-sink.c: after: 66
D: module-alsa-sink.c: Rewound 264 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 264 bytes on render memblockq.
I: module-alsa-sink.c: Underrun!
D: protocol-native.c: Requesting rewind due to end of underrun.
D: module-alsa-sink.c: Requested to rewind 31588 bytes.
D: module-alsa-sink.c: Limited to 504 bytes.
D: module-alsa-sink.c: before: 126
D: module-alsa-sink.c: after: 126
D: module-alsa-sink.c: Rewound 504 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 504 bytes on render memblockq.
I: module-alsa-sink.c: Underrun!
D: protocol-native.c: Requesting rewind due to end of underrun.
D: module-alsa-sink.c: Requested to rewind 33868 bytes.
D: module-alsa-sink.c: Mhmm, actually there is nothing to rewind.
I: module-alsa-sink.c: Underrun!
D: protocol-native.c: Requesting rewind due to end of underrun.
D: module-alsa-sink.c: Requested to rewind 32668 bytes.
D: module-alsa-sink.c: Limited to 292 bytes.
D: module-alsa-sink.c: before: 73
D: module-alsa-sink.c: after: 73
D: module-alsa-sink.c: Rewound 292 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 292 bytes on render memblockq.

```

And consequently the audio skips and clicks. Occasionally, pulseaudio disconnects, killing the stream.

I'm using the latest from Luke's ppa on intrepid.
Any ideas?

EDIT: Ah! Here's an appropriate bug report:[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/268891]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/268891")

---

