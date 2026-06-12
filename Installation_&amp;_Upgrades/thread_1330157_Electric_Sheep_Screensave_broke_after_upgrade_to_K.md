---
title: "Electric Sheep Screensave broke after upgrade to Karmic"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by vayu on 2009-11-18
If I try to run it from the command line it just says "Terminated".

I'm thinking it has something to do with the fact that mplayer, kaffeine and dragon player wont play the AVI files in the .electricsheep directory.  Only VLC will.  Any ideas?  What do I need to have the media players play the AVI files?  What does VLC have that the others don't?

---

### Post by JJRules on 2009-11-19
Yep, same here.

---

### Post by vayu on 2009-12-08
I had to install ffmpeg libraries.

sudo apt-get install ffmpeg libavcodec-extra-52

---

