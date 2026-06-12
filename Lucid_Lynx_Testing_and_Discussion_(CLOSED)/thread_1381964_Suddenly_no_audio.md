---
title: "Suddenly no audio"
date: 2010-01-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by octoberdan on 2010-01-15
At some point after upgrading suddenly no application I tried (mplayer, vlc, rhythmbox) produced sound when I played music files. I ran gnome-control-center (though I'm running wmii) to find that the hardware list was empty.

```

dgreen@dgreen-desktop:~$ lspci | grep audio
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)

```

Thanks in advance!
Dan.

---

### Post by octoberdan on 2010-01-15
Strange, in gnome-session, audio works and the audio device appears in the hardware list for gnome-control-center

---

### Post by octoberdan on 2010-01-15
> **octoberdan said:**
> Strange, in gnome-session, audio works and the audio device appears in the hardware list for gnome-control-center

I was entirely wrong. The audio does not work. The only difference is that the hardware is in the list. It used to be that it would always be in the list, inside our outside gnome-session. 

Also,

> 
dgreen@dgreen-desktop:~$ alsamixer
cannot open mixer: No such file or directory


---

### Post by octoberdan on 2010-01-15
New symptoms. Now, instead of playing in the player, but not producing sound, AND instead of sitting there not making progress, NOW 

```

AO: [pulse] Init failed: Too large
Failed to initialize audio driver 'pulse'
[AO_ALSA] alsa-lib: pcm_pulse.c:732:(pulse_prepare) PulseAudio: Unable to create stream: Too large

[AO_ALSA] Unable to set hw-parameters: Input/output error
Failed to initialize audio driver 'alsa'
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
[AO SDL] using aalib audio driver.
[AO SDL] Unable to open audio: No available audio device
Failed to initialize audio driver 'sdl:aalib'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video

```

---

### Post by dino99 on 2010-01-15
i have sound but not everywhere: no sound with dailymotion, on the other place sound volume is set 0.

Try to reconfigure or purge/reinstall (alsa, pulseaudio)
What logs saying about that?

---

### Post by octoberdan on 2010-01-15
> **dino99 said:**
> i have sound but not everywhere: no sound with dailymotion, on the other place sound volume is set 0.

Try to reconfigure or purge/reinstall (alsa, pulseaudio)
What logs saying about that?

In an act of desperation I purged pulseaudio, installed asoundconf-gtk, copied asoundconf from a jaunty package of alsa-utils into /usr/bin, and switched to ICH7. Probably not a recommended course.

What logs?

---

### Post by VMC on 2010-01-15
$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

also 'alsamixer' works for me.

---

### Post by octoberdan on 2010-01-15
When I switched users and switched to wmii, alsamixer was back to failing, as was sound. I made sure to run asoundconfig-gtk again.

---

### Post by octoberdan on 2010-01-15
Okay, final solution was to remove pulseaudio, remove the reference to "pulse" in /etc/mplayer/mplayer.conf, and add my user to the audio group. Just use alsa, it's easier... I probably could have gotten it working by just adding my user to the audio group at the very beginning.


```

sudo adduser `whoami` audio

```

---

### Post by DougieFresh4U on 2010-01-15
Don't know what 'broke' my sound today. I did run updates this evening and that is when sound quit. When I check for 'Hardware', it shows nothing in Sound.                                                         ```
dougie@dougie-desktop:~$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
dougie@dougie-desktop:~$ alsamixer
cannot open mixer: No such file or directory
dougie@dougie-desktop:~$
```

---

### Post by octoberdan on 2010-01-16
> **DougieFresh4U said:**
> Don't know what 'broke' my sound today. I did run updates this evening and that is when sound quit. When I check for 'Hardware', it shows nothing in Sound.                                                         ```
dougie@dougie-desktop:~$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
dougie@dougie-desktop:~$ alsamixer
cannot open mixer: No such file or directory
dougie@dougie-desktop:~$
```
This is probably worth filing a bug report for. I figured it was just something that I did that messed stuff up. If you need it immediately, I would just remove pulseaudio and use alsa directly. However, having a broken machine may be useful for figuring out a releasable fix for the bug...

---

### Post by AllRadioisDead on 2010-01-16
Same happened to me. I reinstalled pulse and my sound came back.

---

### Post by octoberdan on 2010-01-16
Could it be a matter of configuration? An incompatibility between versions?

---

