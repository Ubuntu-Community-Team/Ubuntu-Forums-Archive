---
title: "Sound stutters after upgrade to Intrepid"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by raccoonone on 2008-11-21
Since I upgraded to Intrepid I started having problems with my audio stuttering. It happens in Songbird as well as Flash applications in FF, and I'm also having problems with the sound completely dying in Pidgin.
All of the problems are intermittent, but the stuttering in Songbird usually occurs every hour or two I would say.

I'm running the x64 version of Ubuntu, and am using the on-board sound of my ASUS P5B Deluxe

I tried looking for solutions but didn't find anything. Any suggestions?

---

### Post by inobe on 2008-11-22
you may be able to locate the packages in synaptic and attempt to update them or reinstall.

i don't know what the ramifications are, you may want to get confirmation first !

---

### Post by raccoonone on 2008-11-22
which packages? I don't even know what's broken

---

### Post by inobe on 2008-11-22
you need to use ```
alsa
``` as the keyword searching in synaptic.

---

### Post by Dan Lyke on 2009-02-09
HP Pavilion dv7-1025nr, when it gets to the login screen I get a repeating stutter on the login sound (which goes on in its bong bong bong way for quite a while).

Done a "sudo apt-get install --reinstall ..." on everything that was installed that came up when I searched for "alsa" in Synaptic, still no joy.

Enough other crap wrong with the Intrepid upgrade that I'm going to wipe and re-install. It's what I had to do with the other laptop, I'm just starting to resign myself to the notion that Ubuntu upgrades don't work.

---

### Post by jervin2 on 2009-02-12
I seem to have the same problem on my Toshiba Satellite A105-2081.  I noticed it when I was trying to use a SIP Softphone.  Totally unusable on this computer.  I wonder if I should wipe this partition and go back to an older version of ubuntu.  What is the process for getting bugs fixed.

---

### Post by unutbu on 2009-02-12
psyke83's [HOWTO: PulseAudio Fixes & System-Wide Equalizer Support](" http://ubuntuforums.org/showthread.php?t=789578")
has a suggestion for what to do if you are experiencing stuttering. Search for the word "stutter".

---

