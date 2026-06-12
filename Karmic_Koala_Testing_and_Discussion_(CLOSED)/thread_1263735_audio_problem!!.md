---
title: "audio problem!!"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SpUpUz on 2009-09-11
i can't hear sound, sound show only internal audio as hardware and do

belloa@belloa-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801AAICH [Intel 82801AA-ICH], device 0: Intel ICH [Intel 82801AA-ICH]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

what can it be?

---

### Post by networm1230 on 2009-09-11
hello 

install all gstreamer plugins

test your sound in the sound configuration

---

### Post by SpUpUz on 2009-09-11
solved :| but i don't know how :)

---

### Post by networm1230 on 2009-09-12
great man! try to go back  (backtrack) and see if you can find out what fixed the sound problem. if you can find the source of the sound fix please share the info with the community. it may help others with sound problems.

---

### Post by feltan on 2009-09-13
I have a similiar problem, as i wrote here too -> [http://ubuntuforums.org/showthread.php?t=1263923](http://ubuntuforums.org/showthread.php?t=1263923) .

When i play audio with my internal audio-card the sound is barely audible even though the volume is set to max.
When i switch audio-output to the external audio-card I can hear from that but not the internal. :confused: 
Strange.

And also, 

when i have a playlist in VLC the audio starts to skip after a few songs. When i have the same playlist in TOTEM the player pauses when going to the next track after a couple of songs.
Anyone else experiencing that?

---

### Post by networm1230 on 2009-09-14
? um.. vary strange. I have not had that problem happen to me. but hearer are same things you may wont to look for.

are all gstreamer plugin installed ?

is you sound card drive installed ?

is your hardware compatible with you OS ?

test your sound sittings/look at the physical hardware for damage

---

### Post by feltan on 2009-09-14
> **networm1230 said:**
> ? um.. vary strange. I have not had that problem happen to me. but hearer are same things you may wont to look for.

are all gstreamer plugin installed ?

is you sound card drive installed ?

is your hardware compatible with you OS ?

test your sound sittings/look at the physical hardware for damage

I have indeed all GStreamer-plugins.
I have looked under hardware-drivers and there's nothing there, it worked great under Hardy Heron, Intrepid and Jaunty and it worked great until the latest PulseAudio-updates.

The external works great, it's just the Internal card that doesn't. The support for Intel´s internal cards has always been superb.

---

### Post by waspbr on 2009-09-14
I am not sure if this is a related problem, but I have noticed some audio issues lately, I use my mobo's internal audio device

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

```

when I boot the computer, it works, then all of a sudden it stops working. I have tried killing Pulse Audio but that didn't help, the card is detected and it is even listed up on the sound preferences. 

The odd thing, is that my usb handset works. So the issue is confined with the internal card.

---

### Post by networm1230 on 2009-09-15
> **feltan said:**
> I have indeed all GStreamer-plugins.
I have looked under hardware-drivers and there's nothing there, it worked great under Hardy Heron, Intrepid and Jaunty and it worked great until the latest PulseAudio-updates.

The external works great, it's just the Internal card that doesn't. The support for Intel´s internal cards has always been superb.

go to the repository (add/remove) and install wine windows emulator. this lat u run windows apps on linux. install windows drives within wine see if that work.[http://www.winehq.org/about/](http://www.winehq.org/about/)

also you may wont to install ( sysinfo ) from the repository this will give you details on your hardware in linux. when installed go to system tools it should be there.

---

