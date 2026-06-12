---
title: "Dropping Audio Frames after Jaunty Upgrade"
date: 2008-12-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gthou on 2008-12-08
Hi, after upgrading to the jaunty development release (through upgrade-manager -d) I'm having issues with the audio dropping frames that seems to be linked to CPU usage (if I open an app such as openoffice or flip my desktop around I hear clicks in the audio).  I haven't experienced this with previous versions.

The issue does not seem specific to any audio application and can be experienced even when playing the test tone from sound preferences.

Where would I start analysing and debugging the issue? I guess best starting point would be to confirm that audio frames are being dropped but I don't know how to view detailed audio output.

Can someone point me in the right direction?

Audio hardware and module info:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Samsung Electronics Co Ltd Device c030
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc320000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

---

### Post by gthou on 2008-12-08
If I change my playback device to 'PulseAudio Sound Server' in System > Preferences > Sound the issue goes away.  This was set to 'ALSA - Advanced Linux Sound Architecture' IIRC I had ALSA set due to issues with ekiga complaining about not being able to open the audio device in Intrepid, but it seems to be not complaining anymore.

---

### Post by psyke83 on 2008-12-08
> **gthou said:**
> If I change my playback device to 'PulseAudio Sound Server' in System > Preferences > Sound the issue goes away.  This was set to 'ALSA - Advanced Linux Sound Architecture' IIRC I had ALSA set due to issues with ekiga complaining about not being able to open the audio device in Intrepid, but it seems to be not complaining anymore.

The ALSA libraries have been patched to remap ALSA output to a running PulseAudio server automatically. 

What this means in practice is that setting the ALSA playback setting in System/Preferences/Sound (which only controls GStreamer applications, by the way) only causes GStreamer applications to play sound to a PulseAudio server via the PulseAudio ALSA plugins (which is less efficient). My advice to you is to keep that setting to Autodetect at all times.

---

### Post by gthou on 2008-12-09
Thanks, I'll try setting to autodetect and see how it goes.

Incidentally, I'm still noticing some occasional dropping of audio frames while playing DVDs with 'PulseAudio Sound Server' as the playback device.

---

### Post by tripinva on 2008-12-12
I hadn't been having this problem and then it just started on me last night after a system update (which fixed a video problem with GLX).  Turns out the update installed PulseAudio for some reason; I had removed it previously because of a similar problem and others.  Killing it and uninstalling it made the problem go away.

PulseAudio: Bane of my existence, when it comes to sound.

- Trip

---

### Post by danf_1979 on 2008-12-14
Put this command in gnome-session to disable pulseaudio at startup. Nothing wrong will happen, and you'll have no more sound problems :).
```

pulseaudio -k

```

If you ever want to give pulseaudio another chance, delete the command from gnome-session, is that simple.

---

### Post by marmuta on 2008-12-14
I've had all audio crackle several times per second with current jaunty and pulseaudio running in a terminal printed lots of buffer under-runs. I suspect the new glich-free code is causing this because when I disable glich-free sound is fine. 

Just edit /etc/pulse/default.pa and add tsched=0 to the line with module-hal-detect, i.e. make it look like this:
```
load-module module-hal-detect tsched=0
```

---

### Post by JACooks on 2009-01-04
> **marmuta said:**
> I've had all audio crackle several times per second with current jaunty and pulseaudio running in a terminal printed lots of buffer under-runs. I suspect the new glich-free code is causing this because when I disable glich-free sound is fine. 

Just edit /etc/pulse/default.pa and add tsched=0 to the line with module-hal-detect, i.e. make it look like this:
```
load-module module-hal-detect tsched=0
```

Thanks, this worked perfectly for my issue as well -- I had PA running correctly per the guide on the forums, but still had issues, usually with flash-based videos.  This has corrected all of these problems.

---

### Post by gnomeuser on 2009-01-04
> **marmuta said:**
> I've had all audio crackle several times per second with current jaunty and pulseaudio running in a terminal printed lots of buffer under-runs. I suspect the new glich-free code is causing this because when I disable glich-free sound is fine. 

Just edit /etc/pulse/default.pa and add tsched=0 to the line with module-hal-detect, i.e. make it look like this:
```
load-module module-hal-detect tsched=0
```

Did you also file a bug on this, in the interest of getting the underlying driver or PA bug fixed so you to might enjoy glitchfree audio and longer battery life?

---

### Post by ShirishAg75 on 2009-01-05
I'm going to file a bug about this, but dunno should it filed against alsa or what?

I am not able to get good sound output and there is crackle and everything while seeing a .VOB in vlc . 

```

[00000460] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Intel'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM iec958:AES0=0x2,AES1=0x82,AES2=0x0,AES3=0x2

```

Filed the same as [lpbug]314003[/lpbug]

---

### Post by marmuta on 2009-01-05
Nope, didn't file. pulseaudio and network-manager make me sad.
I'm going to test again once the OpenAL fix comes through though.

---

### Post by Glowing Fish on 2009-01-20
> **danf_1979 said:**
> Put this command in gnome-session to disable pulseaudio at startup. Nothing wrong will happen, and you'll have no more sound problems :).
```

pulseaudio -k

```

If you ever want to give pulseaudio another chance, delete the command from gnome-session, is that simple.

It looks to me that gnome-session is a binary file with some lines of text, at leas the one I found is.

---

### Post by taavikko on 2009-01-20
> **Glowing Fish said:**
> It looks to me that gnome-session is a binary file with some lines of text, at leas the one I found is.

You tried editing that file? (nano/gedit usr/bin/gnome-session)
that's an executable file, that starts gui, for editing gnome-session properties.

Same which can be opened via System->Preferences->Sessions

---

### Post by Glowing Fish on 2009-01-20
> **marmuta said:**
> I've had all audio crackle several times per second with current jaunty and pulseaudio running in a terminal printed lots of buffer under-runs. I suspect the new glich-free code is causing this because when I disable glich-free sound is fine. 

Just edit /etc/pulse/default.pa and add tsched=0 to the line with module-hal-detect, i.e. make it look like this:
```
load-module module-hal-detect tsched=0
```


This didn't seem to work for me.

---

### Post by BwackNinja on 2009-01-20
Did you restart pulseaudio? Reboot is probably easiest.

---

### Post by vikrant82 on 2009-01-21
Well, I am sure I was having some of that crackling, which seems to be fixed with that fix.

However i am having a lot of these in my pulseaudio logs, 

```

E: module-alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write! Most likely this is an ALSA driver bug. Please report this issue to the PulseAudio developers.
```

anyone else. . ?

---

### Post by marmuta on 2009-01-21
> **vikrant82 said:**
> 
However i am having a lot of these in my pulseaudio logs, 

```

E: module-alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write! Most likely this is an ALSA driver bug. Please report this issue to the PulseAudio developers.
```

anyone else. . ?
Yes, I've seen scores of them while playing with ladspa. The pulseaudio bug tracker has already some of those and the pa-devs routinely point to ALSA for fixes.
[http://www.pulseaudio.org/ticket/420](http://www.pulseaudio.org/ticket/420)

---

### Post by marmuta on 2009-01-21
The new pulseaudio 0.9.14-0ubuntu1 was actually quite an improvement for me (intel8x0/ac97). Before I had nothing but glitches, now they are becoming increasingly rare. I've removed tsched=0 for now.

Now I get for 10 seconds of audio without tsched=0
```
Underruns for  pulse:    1
Underruns for   alsa:    4
Underruns for    sdl:    4
Underruns for openal:   98  # crashed pa

```
Only OpenAl is still totally [borked]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/311853") and even crashes pa after a few garbled seconds.
Oh, and libsdl1.2debian-alsa has to be installed instead of libsdl1.2debian-pulseaudio. Otherwise I get major crackling with sdl apps.

Below is the glitch-counting script I've used. It plays sinewaves which makes the buffer underruns easy to hear. Pulseaudio needs to be restarted manually afterwards, e.g. by typing 'pulseaudio' into a terminal.
```
#!/bin/bash
file=/tmp/sinewave.oga
pulseaudio -k >/dev/null 2>&1
gst-launch-0.10 audiotestsrc samplesperbuffer=1024 num-buffers=431 ! audioconvert ! \
                vorbisenc ! oggmux ! filesink location=$file >/dev/null 2>&1
for ao in pulse alsa sdl openal; do
    (sleep 3; mplayer -ao $ao $file </dev/null; pulseaudio -k ) >/dev/null 2>&1 &
    printf "Underruns for %6s: %4d\n" $ao $(pulseaudio -vv 2>&1 | grep -ci underrun)
done

```

---

### Post by hugmenot on 2009-01-23
My Intel AC&#8217;97 card also gave me bad crackling. It&#8217;s the snd_intel8x0 driver. And tsched=0 fixed it.

Looking here, it appears that upstream knows about it:
[http://www.pulseaudio.org/wiki/BrokenSoundDrivers](http://www.pulseaudio.org/wiki/BrokenSoundDrivers)

---

### Post by marmuta on 2009-01-24
> **hugmenot said:**
> My Intel AC’97 card also gave me bad crackling. It’s the snd_intel8x0 driver. And tsched=0 fixed it.

Too bad, I hoped 0.9.14 was a more general improvement or at least for all ac97 cards. I guess I've been lucky this time that my sound works with or without tsched=0.

---

### Post by pressureman on 2009-01-24
I also have an AC'97 (snd_intel8x0) card, and I have no audio playback problems with Audacious, but I notice that the buddy logon/logoff sounds in Pidgin seem to stutter. Also, I get dropped audio frames in VLC.

Adding the tsched=0 workaround fixes the VLC audio problems, but results in considerably higher CPU util. With tsched=0, pulseaudio uses about 40% CPU, without it, negligible (maybe 2%).

---

### Post by hugmenot on 2009-01-25
For me tsched=1 was worst with flashplugin and simultaneous CPU utilization.

---

### Post by lassegs on 2009-01-29
I've been getting the worst stuttering, with buffer underruns ever since Hardy. Previously ive just silently cursed, and reverted to esound. But now im testing Jaunty, so I decided to stick with it. Still a lot of stuttering. With pulseaudio 0.9.14 the line 
load-module module-hal-detect
already exists, so if you add it to the bottom of the config file pulseaudio crashes at start. Instead youve gotta find this line and just add tsched=0 to the end of it. That fixed _this_ sound issue for me, god knows i have more of them. But like the other guy, now Ive got a lot of these when running pulseaudio -vv:

```
E: module-alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write! Most likely this is an ALSA driver bug. Please report this issue to the PulseAudio developers.
```

---

### Post by zork2 on 2009-02-08
I removed the tsched=0 part and fixed the problem by installing vlc-plugin-pulse. It seems vlc wasn't using pulseaudio by default. 
sudo apt-get install vlc-plugin-pulse fixed it.

---

### Post by pressureman on 2009-02-08
> **zork2 said:**
> I removed the tsched=0 part and fixed the problem by installing vlc-plugin-pulse. It seems vlc wasn't using pulseaudio by default. 
sudo apt-get install vlc-plugin-pulse fixed it.

I already had vlc-plugin-pulse installed, and was using it. It seems that if vlc is left to use "default" audio output, it uses ALSA, which then just gets remapped by the patched alsa libs to go to Pulse. In this mode, I get jerky audio during movie playback, but if I pause playback for a second or two, then resume, the audio is then fine for the rest of the movie.

When setting vlc to specifically use the pulse output plugin, I don't get jerky playback at the start, but now and then the sound stutters right throughout the whole movie (especially during periods of low frequency ambient noise).

But it was the combination of pulse output plugin and tsched=1 that really made the cpu util skyrocket.

---

