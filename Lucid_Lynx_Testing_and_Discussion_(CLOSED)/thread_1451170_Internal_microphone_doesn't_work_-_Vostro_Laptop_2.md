---
title: "Internal microphone doesn't work - Vostro Laptop 2510 - Intel HDA ALC268"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by AKM144204 on 2010-04-10
Testing with an updated Lucid 10.04 Beta, the internal microphone doesn't work for Sound Recorder. I can play music and video sound but not recording with my own voice.

$ uname -r
2.6.32-19-generic

$ cat /proc/asound/card*/codec\#*|grep -i codec
Codec: Realtek ALC268

My ALSA info script is located at
[http://www.alsa-project.org/db/?f=caf13f54adb8f2a7f7c3619b23a90f717b1d3604](http://www.alsa-project.org/db/?f=caf13f54adb8f2a7f7c3619b23a90f717b1d3604)

Also please attached screenshot for
- Sound Preferences
- Multimedia Systems Selector
- ALSAMIXER
- alsa-base.conf script file
- lsmod
- lspci

Please advise how can I solve this?

Thanks & regards

---

### Post by MBHAKM on 2010-04-10
> **AKM144204 said:**
> Testing with an updated Lucid 10.04 Beta, the internal microphone doesn't work for Sound Recorder. I can play music and video sound but not recording with my own voice.

$ uname -r
2.6.32-19-generic

$ cat /proc/asound/card*/codec\#*|grep -i codec
Codec: Realtek ALC268

My ALSA info script is located at
[http://www.alsa-project.org/db/?f=caf13f54adb8f2a7f7c3619b23a90f717b1d3604](http://www.alsa-project.org/db/?f=caf13f54adb8f2a7f7c3619b23a90f717b1d3604)

Also please attached screenshot for
- Sound Preferences
- Multimedia Systems Selector
- ALSAMIXER
- alsa-base.conf script file
- lsmod
- lspci

Please advise how can I solve this?

Thanks & regards

Anybody has any input to resolve this problem. Please advise..

---

