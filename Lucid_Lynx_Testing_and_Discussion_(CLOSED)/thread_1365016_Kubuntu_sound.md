---
title: "Kubuntu sound"
date: 2009-12-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by descendent87 on 2009-12-26
What are other peoples experiences with sound on kubuntu lucid? Since ubuntu switched to pulseaudio I've had nothing but problems with kubuntu & sound. This time I've had to set it to OSS default output as neither PulseAudio or ALSA default output were giving me any sound at all but it still plays up, I have no sound in flash and occasionally amarok or kaffeine will have no sound.
Is it just me or does anyone else think kubuntu should get rid of pulseaudio/alsa completely and just use oss or just stick with alsa and no pulseaudio?

---

### Post by xebian on 2009-12-26
> **descendent87 said:**
> What are other peoples experiences with sound on kubuntu lucid? Since ubuntu switched to pulseaudio I've had nothing but problems with kubuntu & sound. This time I've had to set it to OSS default output as neither PulseAudio or ALSA default output were giving me any sound at all but it still plays up, I have no sound in flash and occasionally amarok or kaffeine will have no sound.
Is it just me or does anyone else think kubuntu should get rid of pulseaudio/alsa completely and just use oss or just stick with alsa and no pulseaudio?

Kubuntu does not use pulse audio.  That's the reason why you are having all these trouble.  The backend for KDE is phonon.  Amarok does not play well with gstream.  It needs only the phonon-backend-xine

---

### Post by descendent87 on 2009-12-26
I have phonon-backend-xine installed and I installed from a Kubuntu daily CD but pulseaudio is listed in the multimedia settings (on closer inspection no pulseaudio packages are installed which would explain why there is no sound if I select pulseadio in multimedia but in that case why does it show up and was selected as default?)

---

### Post by buzzmandt on 2009-12-26
my last install of kubuntu lucid did have pulseaudio and it worked, on 2 computers, a desktop with usb audio and a laptop with intel.  It specifies "playback/recording through the Pulse Audio sound server".  Albeit that wasn't the default  setting, it was there and it did work when i changed it. both computers are set to pulse and no problems at all with sound

---

### Post by VMC on 2009-12-26
> **buzzmandt said:**
> my last install of kubuntu lucid did have pulseaudio and it worked, on 2 computers, a desktop with usb audio and a laptop with intel.  It specifies "playback/recording through the Pulse Audio sound server".  Albeit that wasn't the default  setting, it was there and it did work when i changed it. both computers are set to pulse and no problems at all with sound
Your right it does use pulseaudio. I'm using Kubuntu 10.04 and my sound works fine.

This is my sound card. That might make a difference:
```
Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
```

---

### Post by buzzmandt on 2009-12-27
> **VMC said:**
> Your right it does use pulseaudio. I'm using Kubuntu 10.04 and my sound works fine.

This is my sound card. That might make a difference:
```
Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
```

My audio with the desktop using pulseaudio:
```
Bus 002 Device 003: ID 0d8c:0001 C-Media Electronics, Inc. Audio Device

```

and my audio with the laptop using pulseaudio:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

---

### Post by descendent87 on 2009-12-27
sorry should have said what my soundcard was aswell
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```

---

### Post by brm on 2010-01-01
> **xebian said:**
> Kubuntu does not use pulse audio.  That's the reason why you are having all these trouble.  The backend for KDE is phonon.  Amarok does not play well with gstream.  It needs only the phonon-backend-xine

Cannot agree. Look up the dependencies for kmix. They include the pulseaudio libraries (libpulse-mainloop-glib0, libpulse0).

---

### Post by Zorael on 2010-01-02
> **brm said:**
> Cannot agree. Look up the dependencies for kmix. They include the pulseaudio libraries (libpulse-mainloop-glib0, libpulse0).
Regardless, Kubuntu simply does not use pulseaudio.

KDE *supports* it (nowadays/with patches), but it's not in Kubuntu as a distro.

---

### Post by jetpeach on 2010-01-21
I've heard a lot about how pulseaudio isn't for kubuntu, since phonon is what kubuntu uses instead and serves a similar (although i guess slightly different) function. 

so i had once installed all sorts of pulse stuff on my kubuntu, but then i went to get rid of it and stick to phonon- but as brm said, libpulse0 can't be removed without removing 124 other packages, including many kde packages. why do kdebase-runtime and so many other kde packages depend on pulse if it isn't used by kde?

if i were to venture the answer, but please correct me, i suppose it's because as you said, kde supports phonon. hence, you can configure phonon as the default in the multimedia system settings area. and possibly because, by having the phonon stuff in there, other apps that do depend on it will work seemlessly in kde? this is my best guess, but are there other reasons?

---

### Post by Zorael on 2010-01-21
libpulse0 is (from what I understand) the PulseAudio client libraries. It's not the sound server itself, but rather stuff KDE (et al) needs to interface with it.

I imagine that if you compile KDE yourself, you can configure it to exclude pulse support, and that Kubuntu devs have simply chosen not to explicitly disable it. Pulse isn't part of Kubuntu, but you should still *be able* to use it. If not, that's like saying that Firefox isn't part of Kubuntu, so you shouldn't use it ever and to go use Konqueror.

(As repeatedly stated,) Phonon is not a sound server, but an abstraction layer applications can use to ensure that it will work with whatever sound system is running behind Phonon, as long as that sound system has a Phonon backend installed.

It's also a way to futureproof KDE sound by having their own solution (based on abstraction), instead of associating themselves with a concrete solution that may or may not continue to be developed. That's what happened with KDE3; [ARts](http://en.wikipedia.org/wiki/ARts) was chosen as the default sound server, but development of it died and KDE3 was left with a "defunct" solution.

So this time around Phonon can act as an intermediary, translating multimedia calls using backends, to xine, gstreamer, Pulse, and potentially any other framework.

---

### Post by cookiecruncher on 2010-01-22
My sound works fine. Kubuntu 10.04 on alpha2. No complaints.
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


---

### Post by isilmeraumo on 2010-02-10
I just installed the alpha2 and upgraded it.  I currently have no audio with flash.  Amarok has audio, but huludesktop and Pandora do not.  I have an Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02). Any known help for this?

---

