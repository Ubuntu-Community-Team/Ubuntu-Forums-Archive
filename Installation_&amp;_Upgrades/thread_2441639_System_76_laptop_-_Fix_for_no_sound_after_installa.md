---
title: "System 76 laptop - Fix for no sound after installation"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by jayfulton on 2020-04-25
If this happens your device, pursue pulseaudio and learn about it. Details beow:

After I downloaded and installed 20.04, my System 76 (S76)  GazellePro produced no sound.  Oddly enough, I had posted to twitter about the install, and an S76 support person had liked the tweet.  So I went back and messaged and the support person came back to me very fast with a suggestion about Pulse Audio.  !With that clue, I was able to fix it by adding reinstalling pulseaudio, then adding it to the list of startup apps. 

'pulseaudio --start' was the entry for the startup command

Compliments to the staff at S76 who are proactive and supportive! thanks -Jay

---

