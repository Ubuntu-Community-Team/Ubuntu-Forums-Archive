---
title: "Ubuntu 10.04 Beta 2 ISO Sound Preferences"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2010-04-08
There seems to be a difference between my beta 1 and 2 ISO Sound Preferences. On two different thumb drives I have beta1 and beta2 live installed on them. On the one that had beta2 I do not seem to be able change anything about sound. On my beta1 I can make any king of changes. Any thoughts?

Bill

---

### Post by hrvooje on 2010-04-09
This happend to me too. I use notebook hp nx8220. It has Intel ICH6 with AD1981B . I have no sound. On beta 1 sound was OK.

---

### Post by klytu on 2010-04-09
Similar issue here with Lucid Beta 2 (Sound Preferences shows "Dummy Output" rather than the actual hardware device); and for me I now have no sound. Hardware info:

```
klytu@ubuntu-vistas:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Didn't have this situation previously.

---

### Post by rperkins on 2010-04-09
i have the same problem.  no sound

i had been updating daily since alpha and this issue cropped up recently so I downloaded the beta2 iso and booted from usbdisk.  still no sound.

I use the spdif output of the mobo but I dont think that is the problem because I only see a 'dummy output' as posted by the OP

thanks
rperkins

ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubuntu@ubuntu:~$

---

### Post by mikewhatever on 2010-04-09
Same issue here:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Running 'pulseaudio -k' in a terminal fixed it for me, ...for the session.

---

### Post by Fred2a on 2010-04-09
I've just updated a few minutes ago and I've the exact same thing. Dummy output!

pulseaudio -k worked!

---

### Post by the.scarecrow on 2010-04-09
Exact same problem for me and 

pulseaudio -k

gets the sound working for me as well. Thanks for the tip.

---

### Post by powder on 2010-04-09
Probably due to this bug.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/549738](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/549738)

---

### Post by sparker256 on 2010-04-09
> **powder said:**
> Probably due to this bug.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/549738](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/549738)

Yes that seems to be what I am seeing. From reading the bug looks like they know what is going on so will be fixed soon.

Bill

---

### Post by MBHAKM on 2010-04-09
> **sparker256 said:**
> Yes that seems to be what I am seeing. From reading the bug looks like they know what is going on so will be fixed soon.

Bill

I have the exact same problem when upgraded to Beta 2. Sound Preferences --> Output Connector = Analog Output and Hardware Profile = Analog Stereo duplex, I lost my sound. No sound from music or video. If I select Sound Preferences --> Output Connector = Analog Speaker, then there is a Sound. But I cannot have Voice Call Chat via Skype nor I can do a sound recording with my own voice. IF I play music with Sound Preferences --> Output Connector = Analog Speaker and Hardware Profile = Analog Stereo output, then I can record music.

Anybody has any workaround to do a sound recording with my own voice and do a voice call, so the internal microphone should work?

Please advise

Thanks & regards
AK

---

### Post by sparker256 on 2010-04-09
> **MBHAKM said:**
> I have the exact same problem when upgraded to Beta 2. Sound Preferences --> Output Connector = Analog Output and Hardware Profile = Analog Stereo duplex, I lost my sound. No sound from music or video. If I select Sound Preferences --> Output Connector = Analog Speaker, then there is a Sound. But I cannot have Voice Call Chat via Skype nor I can do a sound recording with my own voice. IF I play music with Sound Preferences --> Output Connector = Analog Speaker and Hardware Profile = Analog Stereo output, then I can record music.

Anybody has any workaround to do a sound recording with my own voice and do a voice call, so the internal microphone should work?

Please advise

Thanks & regards
AK

My problem is with the live beta ISO and not a install. I have used the command  pulseaudio -k and it make my audio work with my live USB ISO.

I would like to find a method to make the command pulseaudio -k be executed automaticly when I boot my thumbdrive as a workaround until this is fixed.

Bill

---

### Post by MBHAKM on 2010-04-09
> **sparker256 said:**
> My problem is with the live beta ISO and not a install. I have used the command  pulseaudio -k and it make my audio work with my live USB ISO.

I would like to find a method to make the command pulseaudio -k be executed automaticly when I boot my thumbdrive as a workaround until this is fixed.

Bill

Oh jesus, I found out the issue with beta 2 for Sound Preferences ---> Analog Output.
On ALSAMIXER, speaker was went muted.

Now the only issue is on Sound recording and Voice call with internal microphone. Hope that works out.
If anybody has any solutions for  Sound recording with own voice and Voice call with internal microphone, please advise..

With regards,
AK

---

### Post by the.scarecrow on 2010-04-09
> **sparker256 said:**
> My problem is with the live beta ISO and not a install. I have used the command  pulseaudio -k and it make my audio work with my live USB ISO.

I would like to find a method to make the command pulseaudio -k be executed automaticly when I boot my thumbdrive as a workaround until this is fixed.

Bill

Hi,
If you press ENTER on the first screen during BOOT, then press ENTER for language and "Try Ubuntu without Installing".

You should find that your sound will then work normally again. It works for me and I got this from the BUG report on Launchpad.

---

### Post by klytu on 2010-04-09
> **the.scarecrow said:**
> Hi,
If you press ENTER on the first screen during BOOT, then press ENTER for language and "Try Ubuntu without Installing".

You should find that your sound will then work normally again. It works for me and I got this from the BUG report on Launchpad.

Thanks! This worked for me as well - just had to un-mute the sound from the volume control after the desktop loaded (when I didn't have sound before, the volume controller was not muted but I could not get sound to function).  I also noticed that pressing ENTER at the first screen bypassed the GUI installer interface and dropped down to a text-based version.

---

### Post by MBHAKM on 2010-04-09
> **klytu said:**
> Thanks! This worked for me as well - just had to un-mute the sound from the volume control after the desktop loaded (when I didn't have sound before, the volume controller was not muted but I could not get sound to function).  I also noticed that pressing ENTER at the first screen bypassed the GUI installer interface and dropped down to a text-based version.

Here is my alsa-info.sh information:

                 By running wget -O ~/Desktop/alsa-info.sh  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)   && bash ~/Desktop/alsa-info.sh from terminal window.
 My ALSA information is located at
 [http://www.alsa-project.org/db/?f=a0...2c668ad1dd14a2]("http://www.alsa-project.org/db/?f=a0e206c71f68386430efdab4b32c668ad1dd14a2").


Please advise if u found anything...

---

### Post by rperkins on 2010-04-10
> **MBHAKM said:**
> Oh jesus, I
On ALSAMIXER, speaker was went muted.


to get my audio working via spdif I installed the gnome-alsamixer and had to ummute the master.

note that the sound preferences did not show the main volume as muted.

yea they gave 'pulse ' the right name as it makes my pulse rise.  alsa met all my needs

---

### Post by MBHAKM on 2010-04-10
> **rperkins said:**
> to get my audio working via spdif I installed the gnome-alsamixer and had to ummute the master.

note that the sound preferences did not show the main volume as muted.

yea they gave 'pulse ' the right name as it makes my pulse rise.  alsa met all my needs

rperkins, wot you had set options snd-hda-intel model=?? in /etc/modprobe.d/alsa-base.conf file, so you get spdif. In gnome-alsamixer / alsamixer, all my settings are unmuted, even also master. I need not have to do anything.

But the problem is I am unable to record . Looks like somewhere problem in the internal microphone.
please advise is there any way / workaround recording works.

---

### Post by MarkieB on 2010-04-12
no longer participating in ubuntuforums.org

---

### Post by sparker256 on 2010-04-18
As of todays daily build 041810 this seems to have been fixed.

The bug referenced in this thread
[https://bugs.launchpad.net/ubuntu/+s...ty/+bug/549738](https://bugs.launchpad.net/ubuntu/+s...ty/+bug/549738)
says fixed released. 

I am marking this thread as solved.

Bill

---

