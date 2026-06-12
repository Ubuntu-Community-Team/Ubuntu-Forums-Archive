---
title: "After upgrade to 14.04 audio became unstable"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by cardogar on 2014-09-24
Dear all,

I have recently upgrade my Ubuntu to 14.04.

Everything worked fine except for the sound system. The audio stops working after a while. I lose the sound after several minutes of Skype use or while watching videos in my browser, it just happens....

But not only Skype or video audio stops, all sounds from Ubuntu stop as well. I need to reboot the system to get the sound back, and then the same, at certain point all sounds disappear. 

I tried many things (reinstall alsa, kill and restart pulseaudio, install pavucontrol) but none of them seems to work.

This is the result of aplay -l
```

card 0: MID [HDA Intel MID], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

The weird thing is that the audio meter of the output sound from pavucontrol shows signal. The bar moves when receiving sound but no sound can be listened.

Typing pulseaudio with or without sound gives me:
```

E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
```

I do not know what else to do. Any help would be more than welcome since I'm really frustrated.

Thank you very much.

---

### Post by Kirboosy on 2014-09-24
Hi there. Perhaps killing off the existing pulseaudio session with ```
pulseaudio -k
``` After that I believe you have to restart the daemon manually ```
pulseaudio -D
```

I'm looking into any hardware specific bugs that may have been reported already about your sound card. I'll let you know as soon as i figure it out.

Hope that helps!
~Caboose

---

### Post by cardogar on 2014-09-24
Thanks a lot for your reply!

I've already tried that without success:

pulseaudio --kill
pulseaudio --start

And no sound until I reboot the system.

In any case, I think that daemon respawns itself after killing it. 

Maybe what happens is that the daemon is not really killed using pulseaudio -k or --kill. I'm going to explore that since I haven't find anything else.

Thanks!

---

### Post by josvanr on 2014-09-24
~$ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.

---

### Post by cardogar on 2014-09-25
I did it. 

~$ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.
~$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

But it doesn't work. No sound.

But I tried some other things. Let's see if that helps to the experts to find a solution...

Using mplayer I get can listen music with both pulse and alsa when the general sound is working. However, once the sound crashes only pulse seems to work:

mplayer -ao pulse test.mp3
Starting playback...
A:   0.2 (00.1) of 242.0 (04:02.0)  0.6% 
...

mplayer -ao alsa test.mp3
Starting playback...
A:   0.2 (00.1) of 242.0 (04:02.0)  0.6% 
Audio device got stuck!
...

I cannot listen the music with any of them (after the sound crash), but once the sound is silenced with alsa I get the message "Audio device got stuck!". If the sound works both outputs (alsa and pulse) are equally fine.

It means that the alsa server is responsible of the problem?

---

### Post by Kirboosy on 2014-09-25
Not sure why but people are reporting success with the following command.

```
pulseaudio -k && sudo alsa force-reload
```

---

### Post by cardogar on 2014-09-25
That command seems to restart pulseaudio and alsa servers... but still no sound.

I'm wondering, which is the difference between doing that and rebooting the system? I mean are pulse and alsa the only servers controlling the sound? is there any other thing that needs to be re-started?

I don't understand why restarting the servers don't bring the sound back and the reboot does...

So far, the only thing that seems to crash when the sound is mute is the mplayer with the alsa option. The message "Audio device got stuck!" is the only difference between the system with or without sound. The rest seems to be Ok, the volume meter of pavucontrol works, alsa lists correctly the devices, mplayer with pulse plays the songs, the sound settings are also OK... frustrating.

---

### Post by cardogar on 2014-09-26
Another side effect I've observed in my computer once the sound crashes and mutes everything: The youtube videos are reproduced in fast motion. I mean you watch the videos much faster than usual...

---

### Post by ancaleth on 2014-10-24
Any new developments here? I am experiencing the same problem, except that the sound sometimes just comes back on even without a restart. I get the same errors with pulseaudio which you described above.

Earlier I was playing a music file in Movie Player; when I stopped the replay, deleted the song from the playlist, and added others, the sound had gone. 
Even before, the sound disappeared upon plugging in headphones. I've noticed a strange clicking sound that somehow seems related to sound being on or off and is pretty much constant when speakers or headphones are plugged in.

Sound has come back on previous occasions upon repeated pressing of louder/softer, mute/unmute. Also sometimes when testing the sound in sound preferences.

> chikoo@chani:~$ pulseaudio -k
chikoo@chani:~$ 
chikoo@chani:~$ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.
chikoo@chani:~$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

The sound has not come back on so far. Before finding this thread, I was playing around with my alsamixer, to no avail, except that the sound icon in the top right corner has somehow disappeared.  

I am running a fresh install of ubuntu 14.04 LTS 32bit, the laptop is quite old though (maybe it's a driver problem?). Directly after the install itself, the speakers were not creating any issues - and it seems to be getting worse and worse. Actually I remember that the first few restarts of the system played a sound upon booting (Which I found strange, because I have been running 14.04 on a 64-bit for months and thought the boot sound had been scratched?). That is no longer the case.

Any help greatly appreciated... maybe my slightly different, but on the whole similiar problem can shed some light on these happenings.

---

### Post by cardogar on 2014-10-24
Not really. I tried thousand of things but nothing changed. Really frustrating.

I give you the most useful links I found, maybe they work for you:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/Users/Troubleshooting/](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/Users/Troubleshooting/)

If you manage to get your sound working, please let us know!

Cheers.

---

### Post by ancaleth on 2014-10-25
Hey, thanks for the links. Luckily my problem seems less complicated than yours.

I went through [http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/Users/Troubleshooting/](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/Users/Troubleshooting/)

It seems pulseaudio was running and loading the devices. But restarting pulseaudio (see post above) was not doing much.

Running 
> mplayer -ao alsa:device=hw=0 yourchosentrack.mp3
immediately achieved sound for that one track played through the terminal.

Then went to: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I was lucky enough for 
killall pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*; ~/.config/pulseto work. Audio for all files, speakers on or out.

Rebooted and all is fine so far. Hope it is permanent.

Thanks again.

---

