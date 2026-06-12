---
title: "No sound in 8.10"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Aqariun on 2008-10-25
Here's the story, I had Vista, then installed Ubuntu as an additional OS.  I installed 8.04.  The sound worked fine, however there were many font issues I couldnt seem to correct, login screen etc.  I had intended to replace Vista but wanted to try ubuntu first.  So to do a clean install I download the .iso for ubuntu.  I thought why not try the beta 8.10.  It fixed all of the fonts issues, :), and everything works fine, except for the sound.  I have gone through many of the suggetions from other threads with no luck, the sound card seems to be being detected, and a driver seems to be loading for it, also, it's a laptop.  I am a total newbie to linux, but usually can accomplish fixing most things on any computer.  Any help would be great, if I cant I will go back to 8.04, but hoping to avoid that.  Thanks

---

### Post by Sealbhach on 2008-10-25
Probably your best bet is to work through this.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It should pinpoint your problem.


.

---

### Post by Aqariun on 2008-10-25
Thanks

Here's my info

aplay -l

card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff01
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


Everything seems to be like it should, although I went through all of the other instructions and still nothing.

---

### Post by thirdspace on 2008-10-25
If you could find a "wav" file and play it with "aplay -v yourfile.wav", and post the output, that would show the route sound is taking (by default) through ALSA, which might give somebody here an idea for a more specific suggestion. If that looks like it works but you hear nothing, odds are there is a hidden volume control somewhere that just needs turning up. HDA Intel devices tend to be equipped with extra, obscurely labelled volume controls, and ALSA is not known for picking intelligent defaults for mixer settings.

---

### Post by Aqariun on 2008-10-25
Here's the results

dan@Laptop:~$ aplay -v CC_0101.WAV
Playing WAVE 'CC_0101.WAV' : Signed 16 bit Little Endian, Rate 32000 Hz, Stereo
ALSA <-> PulseAudio PCM I/O Plugin
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 32000
  exact rate   : 32000 (32000/1)
  msbits       : 16
  buffer_size  : 16000
  period_size  : 4000
  period_time  : 125000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4000
  period_event : 0
  start_threshold  : 16000
  stop_threshold   : 16000
  silence_threshold: 0
  silence_size : 0
  boundary     : 2097152000

---

### Post by kansasnoob on 2008-10-25
NO sound at all I'd look here:

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

Weak sound I'd install:

```
sudo apt-get install gnome-alsmixer
```

It'll then show up in Sound & Video:

[ATTACH]89643[/ATTACH]

[ATTACH]89644[/ATTACH]

---

### Post by phorgan1 on 2008-10-25
I'm in the same situation--no sound since upgrade--sigh...
I've done everything anyone suggests, i.e. checked my drivers checked my mixer settings, everything is perfect and there should be sound, but no joy:(
> 
 aplay -v /usr/share/xulrunner/res/samples/test.wav
Playing WAVE '/usr/share/xulrunner/res/samples/test.wav' : Unsigned 8 bit, Rate 22050 Hz, Mono
ALSA <-> PulseAudio PCM I/O Plugin
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : U8
  subformat    : STD
  channels     : 1
  rate         : 22050
  exact rate   : 22050 (22050/1)
  msbits       : 8
  buffer_size  : 11025
  period_size  : 2756
  period_time  : 125000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 2756
  period_event : 0
  start_threshold  : 11025
  stop_threshold   : 11025
  silence_threshold: 0
  silence_size : 0
  boundary     : 1445068800


Although I've spent much time searching for and trying everything, I would be happy :) to try more stuff;)  Just give me a clue, and I'll try it.

Patrick

---

### Post by Aqariun on 2008-10-26
Well, followed the instructions here

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

and still nothing, peace and quiet might be nice for a while, LOL

---

### Post by marttali on 2008-10-26
if you want sound fast the solution is to install OSS.

---

### Post by isido on 2008-10-26
After the upgrade, I also lost sound. Everything seemed to be ok, but nothing on the speakers. Turned out that the volume levels had changed significantly: I just needed to turn up the physical volume knob.

---

### Post by forcecore on 2008-10-26
i can add that same issue is with my motherboard audio too so it needs fix for final.

[http://ubuntuforums.org/showthread.php?p=6032610#post6032610](http://ubuntuforums.org/showthread.php?p=6032610#post6032610)

---

### Post by Aqariun on 2008-10-26
OMG, I fixed it.  First I reinstalled Ubuntu, then

I added this

options snd-hda-intel model=auto

at the end of this

/etc/modprobe.d/alsa-base

then installed the Gnome Alsa Mixer and all the Gstreamer plugins.

Walla sound.  Not bad for a newbie!

:-({|=

---

### Post by Sealbhach on 2008-10-27
Well done!!!

You didn't give up.:guitar:


.

---

