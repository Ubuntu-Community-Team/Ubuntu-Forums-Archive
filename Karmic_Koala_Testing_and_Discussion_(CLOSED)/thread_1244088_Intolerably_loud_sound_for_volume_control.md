---
title: "Intolerably loud sound for volume control"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zanglang on 2009-08-19
Recently upgraded to Karmic for testing, seems that the new Pulseaudio-based volume control from GNOME is messing up my sound volume...

Previously on my laptop, the audio out was pretty weak so I'd put "Wave" (or was it called PCM Out?) to ~90%, and Main volume at ~70%. After the upgrade where there is only 1 volume control though, I'd have to tune it down to 20-30% or it's too loud (go ahead and guess if I was wearing my headphones that time when I found out... ouch.)

Anyway, I suspect that somewhere Pulseaudio is amping my audio out by several dB. Is there a separate volume normalization thingy that users are supposed to adjust?

Did Totem get a volume normalizing feature as well? For some reason, every time I open an MP3 file with it it reduces my volume by about 30% automatically, with just about falls below the audible threshold because of my problem above. I've had to use Banshee for opening single MP3 files now.

---

### Post by philinux on 2009-08-19
When I reboot sound is always muted. Thats what you get with a development cycle and we are only at alpha4.

---

### Post by DougieFresh4U on 2009-08-19
I have 'gnome-alsa mixer' installed.  I open it and 'tinker' with the different bars while music/sounds are playing.
BUT, some how the main applet seems to get back to 0%. I adjust it and like 2 minutes later it's back to 0% :confused::confused:
This is only happening on my 64 bit partition.

---

### Post by zanglang on 2009-08-19
> **philinux said:**
> Thats what you get with a development cycle and we are only at alpha4.
Yup, that's why I was curious if anyone else was experiencing the same, and if so I'll start digging around to file bugs at Launchpad/upstream. ;)

---

### Post by pressureman on 2009-08-19
My sound also plays at stupidly loud levels. I have the main volume mixer set at 26% (-35.14 dB), and the volume slider in Rhythmbox just one single tiny notch above zero. Any more than that and my head would implode from the sound pressure levels.

I noticed a while back that if I start up alsamixer from a console, the PCM volume is at max level, and no matter what, I can't adjust it there. I can only adjust down the Master volume (can't increase it, not that I'd need to).

I think if I could get the PCM volume level back to some sane level, things would come right.

---

### Post by VMC on 2009-08-19
Mine is very loud also, I just turned the volume down. Never thought of it as a bug. Now maybe I will. In Fedora its the exact opposite.

---

### Post by anders_c_ on 2009-08-19
I have an X-fi soundcard, and if i check in alsamixer it sets both my front and PCM volumes to max with no way to change them. Its ok when i use my speakers but my headphones gets ridiculously loud...

---

### Post by jmmL on 2009-08-19
This is probably the most annoying bug I've experienced in Karmic thus far. I'm pretty sure that the increased volumes are due to the PCM being directly "merged" with the Master channel. I first got wind of it here: [http://ubuntuforums.org/showthread.php?t=1232342&page=3](http://ubuntuforums.org/showthread.php?t=1232342&page=3) . mc4100 gave a link about the change, but it didn't really make the decisions behind the change any clearer for me.

I also experience the loud volume bug. I have to keep the volume at 20% or below (-41.32dB) so I don't damage my ears. Another side-effect of the merger is that PCM is locked at 47, which is too high for my laptop. I get quite a bit of distortion. Previously, in jaunty, I'd set PCM at 30ish and then Master between 70 and 100. This gave me the volume I required without the distortion.

---

