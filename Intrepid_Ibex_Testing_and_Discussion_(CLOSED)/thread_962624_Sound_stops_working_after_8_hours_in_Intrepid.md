---
title: "Sound stops working after 8 hours in Intrepid"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chris4amd on 2008-10-29
I'm up all day using my computer without issue, sound in flash video, exaile, etc.  I go to bed, get up, and sound doesn't work in any application.

Attempting playback from the command line:
> 
XXXX@XXXX:/media/My Book/Audio/Buzz Bin$ aplay 001\ ifyouthinkthisworldisbad.mp3 
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
aplay: main:583: audio open error: Device or resource busy


Relevant section of lspci:
> 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)


lsof /dev/dsp indicates that nothing has ahold of my sound device though.

Restarting alsa-utils and pulseaudio daemons don't affect the problem.  After a reboot the issue is resolved for another 8 hours.

Any suggestions to keep sound around longer than a day?

---

### Post by jfernyhough on 2008-10-29
Issues seem to have appeared with PulseAudio; there are a number of people reporting problems.

I haven't had any yet with 0.9.10 on my laptop - but then it gets turned off regularly. I did, however, have problems with PA freezing when I was testing 0.9.13.

---

