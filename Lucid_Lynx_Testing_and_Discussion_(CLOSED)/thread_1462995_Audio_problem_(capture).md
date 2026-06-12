---
title: "Audio problem (capture)"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Scott82 on 2010-04-26
Hi, I just installed the RC of Kubuntu to give it a shot, and it's having a problem with audio capture... I have Intel_HDA or whatever, i'll check when it's done reinstalling. basically, in just about any distro, the sound isn't working right. from just doing a pc beep when should be playing back to a incredibly distorted audio capture that's usually solved by turning 'Digital Mic' all the way down (seems to be basically Mic Boost). But with Kubuntu 10.04 RC, turning it down doesn't get rid of all the distortion, I tried turning down / muting everything that i don't know what is, and lowering all other things that I know have to do with the mic to the minimum or muting them, and i still records distorted.

the really annoying part of this, is it worked perfectly without adjusting any settings at all in BETA 1 & 2. so anyway, right now I'm reinstalling BETA 1 and gonna hope that it still works after installing updates.

sorry for the typo's, trying to catch as many s i can, writing this on my sons pc and the keyboard buttons are really really sticky.:lolflag:

anyhoozels, I'll write back again after trying updating from Beta 1. I really hope that it starts working again, because this was the only disro that I was able to get every aspect of the sound working before (one incredibly common problem is the distos that I can't change audio to my usb headset, that's only worked in ubuntu and kubuntu 10.04 so far).

EDIT::
I realized that I installed the 32 bit version. then realised that all the distrobutions that i have the capture distortion in were 32 bit. so for my audio capture to work properly i need 64 bit linux. still don't know for sure why the playback does a pc beep in some distros, i think it's the older kernel that causes that.

---

### Post by dino99 on 2010-04-26
is your sound driver correctly recognized ? (system pref sound)

a nice package can help a lot : gnome-alsamixer and dont forget that one too : paprefs


[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Scott82 on 2010-04-26
can't install gnome-alsamixer in kubuntu without installing a ton of other gnome packages, and kubuntu doesn't use pulseaudio (one of the best things about kubuntu over ubuntu... pulseaudio uses about 9 to 18% of my processor each time sound is playing in ubuntu).

anywhoo, seems like it wasn't because of the 32-bit.... getting the distortion in 64 bit after upgrading from beta 1.... does work absolutely fine in beta 1 though. also did through beta 2 if i remember right.

---

