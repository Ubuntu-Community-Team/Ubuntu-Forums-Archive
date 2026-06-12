---
title: "Karmic, Audio &amp; Smokin' Guns"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yeti can't ski on 2009-10-25
Smokin' Guns is a very nice Western Quake3 mod that I used to play without any problems with Jaunty. 

With the upgrade to Karmic Beta 32Bits I am having a serious audio problem. Sound will only work for fractions of a second and then I get only strong static (just like a giant fly moving around your head). 

I tried to remove pulseaudio following Jaunty tutorials, but then the system was unable to access ALSA with System>Preferences>Sound and my computer was soundless. It seems that Karmic cannot live without pulseaudio as easily as Jaunty. So I had to reinstall it. 

I also ran the ".exe" of game with Wine and sound worked but not only it is not a Linux native solution but performance was crappy. 

Any ideas? Should I file a bug? If yes, could someone please give me more directions on how to file it properly?

Thanks in advance.

**Edit1:** So, I found out that Pulseaudio is much more deeply interwoven with Karmic than it was with Jaunty. Karmic's audio just doesn't seem to work properly without Pulseaudio: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465)

Without pulseaudio the audio of the game will work perfectly, but all the rest of Ubuntu will be soundless. Hard choices...

**Edit2:** Okay, I found a workaround which is less traumatic than removing pulseaudio and losing sound control. There is a way to stop pulseaudio with "killall" and preventing it from coming back to life during the same session. I just followed this thread (comment of trendzetter): 

[http://ubuntuforums.org/showthread.php?t=1306356]("http://ubuntuforums.org/showthread.php?t=1306356")

---

