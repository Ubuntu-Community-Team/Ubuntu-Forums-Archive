---
title: "No Sound after some tinkering"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by pajoohesh on 2009-11-30
Hi Folks,

My sound was working OK in karmic but I started some changes in the drivers and it does not work any more. Is there any way to revert every thing to the installation condition?

I have tried 
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
```
with No Success.:(

any solution?

---

### Post by pajoohesh on 2009-12-01
Really no way?

It is very difficult to reinstall.

---

### Post by pajoohesh on 2010-01-13
Problem solved. 

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

By reinstalling the drivers and also changing the Hardware - Profile Tab in Sound Preferences.

Tough Times...
:D:D:D

Sorry for the duplicate

---

