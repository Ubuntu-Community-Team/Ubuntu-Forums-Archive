---
title: "No Sound from TV Tuner (HVR 950Q)"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fogNL on 2009-10-08
Installed Ubuntu 9.10 beta 64bit last night doing a fresh install.  Everything works except for the sound from my Hauppauge HVR 950Q USB tv tuner which worked fine in 9.04 64bit.

Installed TVtime, pick up and play channels no problem.  Opened up the new audio panel in Gnome, and checked the output for the tv tuner, and its showing that it is registering sound (the meter goes up and down related to the channel) but nothing is coming out.  Tried using mplayer too, same issue.  Everything *appears* to be unmuted.

Its probably something simple with a new way of doing things, but I can't seem to find the option to output it to my speakers.

---

### Post by fogNL on 2009-10-09
No one else has come across this?  Maybe i'm doing something wrong?  Any suggestions would be helpful.

---

### Post by rajeev1204 on 2009-10-09
> **cquilliam said:**
> No one else has come across this?  Maybe i'm doing something wrong?  Any suggestions would be helpful.

I have a problem where tvtime wont pick up signals sometimes and unless i reboot, i cant watch tv.

---

### Post by fogNL on 2009-10-09
> **rajeev1204 said:**
> I have a problem where tvtime wont pick up signals sometimes and unless i reboot, i cant watch tv.

It appears that everything with the tv tuner itself is working fine.  Running tvtime, switching through channels, etc. Even the Ubuntu sound panel shows audio output coming from the tv tuner, but I just don't hear anything.  All other sounds on the system works.  Its like the sound isn't being routed properly.

---

### Post by ppjose on 2009-10-09
hi, 

I have the same problem with my tv tuner analog and tvtime 

 I have only sound if i run the test in gstreamer options

greetings

---

### Post by scorchedbysun on 2009-10-10
I have the exact same problem with a HVR-900 tuner (EyeTV Hybrid). There is image, but no sound.

The new sound settings panel is showing that sound is coming in (the meter is moving up and down) but that's it.

Thanks.

---

### Post by fogNL on 2009-10-14
I've been trying to figure this out for the last few days, and I can't get anywhere with it.  I have no idea where to look anymore.

---

### Post by MaximCarnage on 2009-10-15
from this thread [http://newyork.ubuntuforums.org/showthread.php?p=7728128](http://newyork.ubuntuforums.org/showthread.php?p=7728128) 

I got TV-Time to work WITH AUDIO by Making a script-file with:

> #! /bin/sh

nice -n 0 tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

My problem is that i can't figure out how to get VLC to get the audio. I wanna capture from a composite source and save it. I can get the Video just fine but no matter what I have tried I cant get the audio.

When i select the device in pulse and start up VLC(V4L2) i can see pulse audio in volume fluctuating but VLC in not recieving the data. 
Like someone said this appears to be a routing problem.

Has anyone a clue on what to do ?

---

### Post by rajeev1204 on 2009-10-15
Solved it guys !!!!!!!!!!!

There is something called amixer and i used the command

```
amixer -c 0 sset CD,0 80%,80%  unmute
```


I have used CD because my tvtuner sound output is connected to CD IN of motherboard.


Note: These settings are lost on restart.Iam going to file a bug.

---

### Post by MaximCarnage on 2009-10-15
> **cquilliam said:**
> I've been trying to figure this out for the last few days, and I can't get anywhere with it.  I have no idea where to look anymore.

> **rajeev1204 said:**
> Solved it guys !!!!!!!!!!!

There is something called amixer and i used the command

```
amixer -c 0 sset CD,0 80%,80%  unmute
```


I have used CD because my tvtuner sound output is connected to CD IN of motherboard.

What if we are on a laptop what should we use ?

---

### Post by rajeev1204 on 2009-10-16
> **MaximCarnage said:**
> What if we are on a laptop what should we use ?

Well.if your laptop comes with a tuner card built in, you need to check your manufacturer manual to figure out which volume slider you need to unmute.

---

### Post by fogNL on 2009-10-20
> **MaximCarnage said:**
> What if we are on a laptop what should we use ?

Yeah, same thing here.  My TV Tuner is connected via USB.  I'm not sure if its a problem with the audio panel or with the usb audio driver or what.  I may have to install Kubuntu 9.10 and see if it works in there.

---

### Post by fogNL on 2009-10-21
Yeah, I have no idea what to do.  I can't figure it out at all.  That little script that MaximCarnage has there works, but of course the audio is lagged from the video which is equally as useless.  So, it seems that yet again, PulseAudio is the culprit.

---

