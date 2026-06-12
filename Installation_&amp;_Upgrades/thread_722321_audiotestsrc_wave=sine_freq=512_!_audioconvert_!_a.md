---
title: "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profi"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by eatblueorange on 2008-03-12
I get this error after upgrading feisty to gutsy when I test the sound from system->preferences->sound. 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: no element "gconfaudiosink".  

 I have already read some of the posts here and from the internet and even reinstall alsa, compile but still i get this error when i try to test the sound or whenever i play the totem player.  The only working sounds that i hear are the system sounds, and the music works from xmms player.  I don't know if this has to be the culprit of gstreamer, coz when I run gstreamer-properties from the terminal, I get this errors:

gstreamer-properties-Message: Skipping unavailable plugin 'autoaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'osssink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'autovideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4l2src'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'osssrc'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'


I installed and reinstalled gstreamer and all its plugins.  I don't know why some applications, like games really depend on gstreamer.  I installed totem-xine and I can play now my mp3s's and movies via totem player but i still  cannot hear sounds from applications that uses alsa or gstreamer framework.  I installed open sound system (OSS)  and I can hear now, the sounds from some of the applications like openarena but some applications that uses alsa in their configuration doesn't produce a sound and also this time, the system sounds doesn't produce a sound either.  How do i correct this thing? does anyone there has the same problem as mine?  please share your solutions.  In feisty, everything was OK, but why when we upgrade, we had this problem, does this mean that everytime we upgrade ubuntu, we would fresh install it? I don't want fresh install coz i already have installed many softwares from my previous feisty and it would take longer to install them.  I don't know if ubuntu is a pain in the *** or do i have to switch to other linux destribution? help me.

---

### Post by cmnorton on 2008-03-13
I got this too, and am wondering what's up.

---

### Post by cmnorton on 2008-03-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/122560](https://bugs.launchpad.net/ubuntu/+bug/122560) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				 I got my Thinkpad T61p's sound working by adding the following to the end of /etc/modprobe.d/alsa-base

options snd-hda-intel model=thinkpad-t61p

There was no magic list containing my model number. Someone else had a problem with their Dell; and added this line

options snd-hda-intel model=dell-m26

Basically, I put a dash in between the brand and the model and took a guess. I now have sound.

---

