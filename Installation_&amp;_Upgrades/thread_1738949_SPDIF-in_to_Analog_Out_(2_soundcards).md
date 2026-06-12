---
title: "SPDIF-in to Analog Out (2 soundcards)"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by api984 on 2011-04-25
Hello,

I am trying to make the following **audio schema:**

**SoundCard 1:**
 -Optical IN (IEC958 input) 
   -Xbox360 Connected for SoundInput

**SoudCard 2:**
 -SB Live 24bit Exernal
  -5.1 speakers 

Is there any way to do REALTIME audio playing from SoundCard 1 to SoundCard 2.

I suppose in the middle we need some DECODING (PCM sound, AC3).

**Final Schema:**
Xbox360 (OpticalOut) -> SoundCard1 (opticalIN) -> DECODE (Ac3, PCM) -> SoundCard2 (AnalogOut) -> 5.1 Speakers

This worked well while I was in Windows playing with GraphEdit. Now I am trying to make the same here. 

can I CAT output to any audio player in CLI? or something alike.
-trying with - mplayer, jackd, vlc to get SPDIF IN.

---

