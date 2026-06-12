---
title: "Mic partially works on netbook w 12.04"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by jeppex on 2012-07-12
Hi

So Im helping out my girlfriend getting rid of Windows XP on her Netbook. She needs it for travelling so the basics has to work.

The one thing I can't seem to fix is to get the mic properly working. When Im using Sound Recorder I can hear that the Mic is working in some sense. I can record sound at least. 
However it doesnt in Skype or Google Chat. In empathy I can hear my voice echoing alongside the one I am talking to, but the one I am talking to cannot hear anything, ie. the mic works but it is not being transmitted?

The Netbook is an emachine em250 series. I installed Ubuntu from Windows using the wubi feature.

Any ideas as to what the problem, and hopefully solution, to this might be?

All the best
Jeppe

---

### Post by jmfal on 2012-07-12
Welcome to Ubuntu

Open alsamixer in a terminal

```
  alsamixer     
```

Press F5 All

navigate to  "mic" and unmute by pressing  "M" or "m" and increase control by using up/down arrows on keyboard.

I don't use skype or chat, so there may be more to configure than that.

---

### Post by jeppex on 2012-07-12
Thanks for that! However I didnt work. I guess the Auto-Mute should be disabled as well?

So, there is no sound at all in Empathy from the microphone. Still I can record from the mic in Sound Recorder. 

I really don't know what to make of this and I would hate to turn this Netbook back accompanied by a "sorry, Windows seems to support it the best". 

Any other ideas?

---

### Post by jmfal on 2012-07-12
Take a look at this , sorry  I couldn't help

[http://ubuntuguide.org/wiki/Ubuntu_Precise_Internet](http://ubuntuguide.org/wiki/Ubuntu_Precise_Internet)

---

### Post by jeppex on 2012-07-12
I will. Thanks for your help :)

---

### Post by tooplanx on 2013-01-02
Hiya,

I'm having exactly the same problem with my emachines e250 netbook. I'm using Zorin OS 6 (based on ubuntu 12.04) which is awesome, but this problem is the first make or break issue I've come across.

I tried everything on here and looked at that link but couldn't see anything that seemed to refer to this problem. 

Anyone managed to solve this yet?

---

