---
title: "Problem - All sounds muted on playback"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kolslorr on 2009-04-17
Hey folks,

Ater upgraded to Jaunty alpha 2 weeks ago, I lost all sounds, and my googling tells me this is a common problem with the new pulseaudio module. I thought RC release will solve it but sadly no. So here's my situation and I hope someone can help...

Boot up of the default Ubuntu drumming sound is muted.

Running any mp3 or movie or sound file will not give any errors, it runs but all sound is muted. No errors are shown on command line window too.

I tried aplay xx.mp3 on command line, it also shows it started to run without errors.

While mp3 is playing on Rythmbox for example, I can see that the system is actually playing the music through its visualization window, but somehow all sounds muted.

I have used gnome-alsamixer to adjust every playback slider to 100% (Master, PCM, Front, etc), and confirm none of them has mute checked.

please pleas help me.... :(

```
$ lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
^[[6~card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by kolslorr on 2009-04-18
No one else have this problem? 

and this thread is pushed all the way back. :(

---

### Post by knavarathna92 on 2009-04-18
I have the same exact problems and the same exact hardware, I thought I had it solved when I reinstalled ALSA but the problem resurfaced again.  Help greatly appreciated.

---

### Post by kolslorr on 2009-04-18
worst part is, launchpad can never launch in my browser, it gets timeout all the time.

---

### Post by cooldudeman01 on 2009-04-18
I just upgraded to Jaunty a few hours ago, subsequently all my sounds were muted.  So, I played with the sound settings, and it turned out that pscp (Alsa mixer) was muted.  So I turned the volume up, now I get sound....all crackly sound all the time.  Here's my output, I'm running a Dell D620.

lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

### Post by cooldudeman01 on 2009-04-18
So my screetching seems to be resolved now if I change to using OSS instead of Alsa.  

Change this in System -> Preferences -> Sound playback and pick some of the OSS entries and do a test instead of the "Autodetect" which is apparently autodetecting non-good ones.

I had to change Sound Events, Movies, and Audio Conferencing in order to make it work for all sound playback.

As for kolslorr - what I would try doing is turning up the volume on everything in the volume control / sound preferences.  There's usually several devices that have sound control depending on your hardware.  Also the preferences button has a bunch more controls, one is called PCM and in my experience about every time I've installed or updated Ubuntu that PCM is all the way down for some reason.

---

### Post by cooldudeman01 on 2009-04-18
So it isn't fixed... although it appears that way if I'm only doing the test sounds from the sound preferences menu.  Video playback and sound is still screetching, it's terrible and unusable.  Does anyone have any ideas?

---

### Post by kolslorr on 2009-04-18
> **cooldudeman01 said:**
> So my screetching seems to be resolved now if I change to using OSS instead of Alsa.  

Change this in System -> Preferences -> Sound playback and pick some of the OSS entries and do a test instead of the "Autodetect" which is apparently autodetecting non-good ones.

I had to change Sound Events, Movies, and Audio Conferencing in order to make it work for all sound playback.

As for kolslorr - what I would try doing is turning up the volume on everything in the volume control / sound preferences.  There's usually several devices that have sound control depending on your hardware.  Also the preferences button has a bunch more controls, one is called PCM and in my experience about every time I've installed or updated Ubuntu that PCM is all the way down for some reason.

I have already tried that, doesnt work either...

:(

---

### Post by Languid Heap on 2009-04-18
Check /var/log/messages and see if you find something like "hda_codec: Unknown model for ALC883, trying auto-probe from BIOS..."

If you see a message like that (but with your chipset) check out this HOWTO to fix it [http://ubuntuforums.org/showthread.php?t=801541](http://ubuntuforums.org/showthread.php?t=801541)

The problem that thread addresses is when the auto-probe guesses the wrong model. In my case, the wrong model provided the wrong tracks in the mixer, which prevented me from unmuting the right tracks.

Good Luck!

---

### Post by crimsun on 2009-04-19
> **kolslorr said:**
> Ater upgraded to Jaunty alpha 2 weeks ago, I lost all sounds, and my googling tells me this is a common problem with the new pulseaudio module. I thought RC release will solve it but sadly no. So here's my situation and I hope someone can help...

Please run `ubuntu-bug pulseaudio', and tell us the bug number that was reported.

---

### Post by Simrn on 2009-04-19
I'm also facing somewhat the same problem, everytime I reboot, all mixer controls go mute as a result I can't hear a single sound :(. To help I go to system > preferences > sounds then adjust different sound settings but still it does not seem to help, no sound on playback works. My friend told me to Right click on the speaker - Volume Control: Nvidia CK804- and all settings adjust to off/minimum under Playback tab. Fix the sliders and I would have sound perfect, but it too didnt work for me. Quite helpless.

---

### Post by kolslorr on 2009-04-19
> **crimsun said:**
> Please run `ubuntu-bug pulseaudio', and tell us the bug number that was reported.

I wish I can, but launchpad is taking forever to load, and I had been trying for past few days.

EDIT* The launchpad problem appears to be my local ISP proxy screwup, some of the U.S sites are completely crippled since last week. I used a webproxy and I can access launchpad now.

---

### Post by knavarathna92 on 2009-04-19
Something interesting, I can get sound well the first few seconds I plug in my headphones (If I plug in while a video or song is playing, I get 10 secs, If I plug in from boot, I go up to login sounds) but then sound slowly dims until the point I can't hear anything.  Gnome-alsamixer shows all sliders on full.

---

### Post by kolslorr on 2009-04-19
I give up on Launchpad.

So I am able to finally get to the Report Bug window, and it ask for a summary before I can click Continue to submit. I typed in something, hit continue, and I am brought back to the same page.

I will wait for someone else to submit this bug. this is damn sad.

---

### Post by philhughes on 2009-04-19
I had a similar problem with ALC882 hardware. I just got faint crackles instead of sounds. In my case the problem was solved easily.

Right click on the volume control, Open volume control, make sure that the Device is HDA Intel (Alsa mixer). The PCM setting (and a couple of others) was set to 0. Set this to some level and the sounds played.

---

### Post by knavarathna92 on 2009-04-19
> **kolslorr said:**
> I give up on Launchpad.

So I am able to finally get to the Report Bug window, and it ask for a summary before I can click Continue to submit. I typed in something, hit continue, and I am brought back to the same page.

I will wait for someone else to submit this bug. this is damn sad.

I finally got a solution! This worked for me and we had similar problems so maybe it will help you. (NOTE: I did this after manually upgrading pulseaudio and ALSA)

open up a terminal
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this line at the end of the file
```
options snd-hda-intel model=3stack
```
save and reboot, sound should be back to normal.  Hope this works.

---

### Post by kolslorr on 2009-04-19
> **knavarathna92 said:**
> I finally got a solution! This worked for me and we had similar problems so maybe it will help you. (NOTE: I did this after manually upgrading pulseaudio and ALSA)

open up a terminal
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this line at the end of the file
```
options snd-hda-intel model=3stack
```
save and reboot, sound should be back to normal.  Hope this works.

Thanks, i just tried but its the same...

what steps did you use to upgrade pulseaudio and alsa?

---

### Post by knavarathna92 on 2009-04-20
theres a script for ALSA here: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

And this guide has the links to a PPA containing new pulse audio files:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by knavarathna92 on 2009-04-20
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)
 this is a helpful guide for sound issues, may be of use as a lot of things he stated to be switched on by default were not on my computer.

---

### Post by kolslorr on 2009-04-21
> **knavarathna92 said:**
> theres a script for ALSA here: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

And this guide has the links to a PPA containing new pulse audio files:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Did both, but still no sound.

I wonder whats the problem with Alsa in Intrepid, that they need to come up with this Pulseaudio to confuse users...

:(

---

