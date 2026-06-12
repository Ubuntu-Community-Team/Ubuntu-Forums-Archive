---
title: "need clarification on Webcam audio."
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by executorvs on 2010-03-15
I have a [s]M$[/s] MS vx-3000 and it works mostly out of the box, not the audio though.

my questions are:
a. does anyone know if the gspca driver also is used for operating the mic?
b. if not does anyone know what is?
c. I seem to recall some usb audio devices being blacklisted in earlier ubuntu versions. while my usb webcam mic seems to be detected I though I should check. Does anyone else remember where the pertinent blacklist might be?

this seems to be the last big hurdle in out of the box functionality for the vx-1000 and vx-3000 webcams and I would like to make sure I address any issues to the right place on launchpad. I just don't know what could or should run the mic.

---

### Post by executorvs on 2010-03-16
any ideas? anyone?

---

### Post by cariboo on 2010-03-16
If your web cam is anything like my Logitech, check sound preferences for a usb input device, and select it when using the web cam.

---

### Post by cristianrosa on 2010-03-16
I have a laptop with no built-in mic on it, but I use an Hercules Dualpix Exchange webcam that has a mic, and each time I plug it, I have to select it from Sonund Preferences.
Is there a way to keep this setting between plugging/unplugging?

---

### Post by executorvs on 2010-03-16
unfortunately the sound preferences was one of the first things I checked and while it is displayed and selected it doesn't seem to be capturing or detecting any sound. my next step was to install gnome-alsa-mixer and double check there and everything there checks out. 

the thoughts mentioned above are all I can really think of at this point.

is there a way to query the system for audio device information?

---

### Post by kyleabaker on 2010-03-17
> **executorvs said:**
> unfortunately the sound preferences was one of the first things I checked and while it is displayed and selected it doesn't seem to be capturing or detecting any sound. my next step was to install gnome-alsa-mixer and double check there and everything there checks out. 

the thoughts mentioned above are all I can really think of at this point.

is there a way to query the system for audio device information?

I've got a vx-1000 webcam and pre-Ubuntu 10.04 I was unable to get it working (x64) at all. I don't expect you'll get much help with the microphone as it seems to be a very common issue. I've been searching for a while now and haven't found anything remotely close to solving the mic issues.

My mic is apparently detected as well, just not registering any input. If you find a solution or that blacklist you mentioned, please let me know!

---

### Post by executorvs on 2010-03-17
The "blacklist" point I mentioned wasn't actually a blacklist, after some digging I was reminded that what I was thinking about was a line in alsabase.conf to prevent usb audio devices from setting themselves as default. I changed said setting just to see and it had no effect. I've been playing with this webcam on and off for about a year and a half now. I have little problem with the video at this point. The older microdia driver might be blacklisted as the newer gspca driver is included and used.

sound wise I've checked every setting I can think of alsa-mixer, padevchooser, gstreamer-properties, asoundconf-gtk(couldn't get this one to load), paprefs, and gnome volume. camera is shown in all, set as default input in all, capture and volume are turned up in all, and still nothing.

I've also checked every place I can think of to make sure it's detected.
@comp:~$ arecord --list-devices gives
card 1: camera [USB camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

@comp:~$ cat /proc/asound/camera/stream0
USB camera at usb-0000:00:12.0-1, full speed : USB Audio

Capture:
  Status: Stop
  Interface 2
    Altset 1
    Format: S16_LE
    Channels: 1
    Endpoint: 4 IN (NONE)
    Rates: 8000, 16000

@comp:~$ cat /proc/asound/pcm
01-00: USB Audio : USB Audio : capture 1

@SDF-1:~$ lsmod | grep snd gives a longer readout but you get the idea. everything sees it and tells me it should work and I'm at a total lose as to what else to check.

---

### Post by kyleabaker on 2010-03-24
Still no progress?

---

### Post by executorvs on 2010-03-24
still none. I'm hoping to have a little more time next week as I'll have some time off. with luck maybe Someone will find a way to get it working soon.

---

### Post by gordintoronto on 2010-03-25
No chance it's muted in Volume Control?

---

### Post by kyleabaker on 2010-03-25
> **gordintoronto said:**
> No chance it's muted in Volume Control?
As far as I can tell, its not muted. I've checked several different ways.

---

### Post by executorvs on 2010-03-25
> **executorvs said:**
> sound wise I've checked every setting I can think of alsa-mixer, padevchooser, gstreamer-properties, asoundconf-gtk(couldn't get this one to load), paprefs, and gnome volume. camera is shown in all, set as default input in all, capture and volume are turned up in all, and still nothing.

No, it's not muted in volume control as was stated earlier in the thread.

---

### Post by Guitar John on 2010-04-04
I'll be watching this thread.  I have the same problem with a Hercules Dualpix USB 2.0 HD720p.  

I have video & working sound on my Dell D610 running Xubuntu 9.10, but the 1.86 GHz processor cannot keep up with the video unless I reduce the resolution to something like 320x240.  

I tried using my sister-in-law's newer computer, which has Ubuntu 9.04, and Dual 2.0 Ghz processors.  Video at full resolution, but no sound.  I tried every possible combination of ALSA and Pulse Audio.

---

