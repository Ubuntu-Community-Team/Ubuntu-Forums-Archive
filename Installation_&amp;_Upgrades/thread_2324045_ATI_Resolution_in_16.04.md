---
title: "ATI Resolution in 16.04"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by felipe32 on 2016-05-10
Well, I guess it kind of falls on the same subject here...
I am very new to Ubuntu and Linux, so...
I own the same MB and I'm using my PC mainly as an HTPC. The thing is, I noticed the overall visual quality is lower than I had on Win7 and it seems the audio quality is also a little lower.
Is it normal, or do I have to install the proper drivers for audio (VIA 1708S) and video (Radeon HD4200)? For my surprise, Ubuntu installed everything on its own and using Kodi I was able to watch movies and even use DTS and AC3 passthrough and all...but, as I said, they're not as good as they were on Win7...

Thanks in advance!

---

### Post by QIII on 2016-05-10
Moved to its own thread from [http://ubuntuforums.org/showthread.php?t=2322659](http://ubuntuforums.org/showthread.php?t=2322659)

---

### Post by Mark Phelps on 2016-05-10
Sorry, but a problem you're going to have is that AMD dropped the fglrx Linux driver support for their HD4x-series cards years ago, and even if you could find the drivers today, they will not work in any recent Ubuntu version.

You will be relegated to using the default open-source drivers, and while those work OK for routine 2D stuff, I don't know how well they will work for HTPC stuff.

Good Luck

---

### Post by felipe32 on 2016-05-10
> **Mark Phelps said:**
> Sorry, but a problem you're going to have is that AMD dropped the fglrx Linux driver support for their HD4x-series cards years ago, and even if you could find the drivers today, they will not work in any recent Ubuntu version.

You will be relegated to using the default open-source drivers, and while those work OK for routine 2D stuff, I don't know how well they will work for HTPC stuff.

Good Luck

Thanks, man.
I looked for ATI drivers and, like you said, I noticed their newest catalyst does not support my video card. I haven't found anything on the sound card though...

And it's not something insufferable. It kinda makes it uncomfortable to use the browser, facebook and stuff like that on a big screen, and I noticed music playback isn't as good as it was on windows. But for it's main purpose, I guess it doesn't mean that much. I assume the audio pass-through for movies shouldn't change too much, but I wonder if there is anything I could do to improve music playback a little (I'm using the standard music player on Ubuntu 16.04). Do you think the via software that was running on windows could be the one making the difference? Is there anything I could do to tweak audio output for music playback, like an equalizer or something?

---

