---
title: "Sound Problem"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by garymadden on 2005-10-30
Hi!

Hoary didn't properly detect my sound card. I used modprobe to properly install my sound card but there still is no sound.

aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: rev20 [VIA 82C686A/B rev20], device 0: VIA 82C686A/B rev20 [VIA 82C686A/B rev20]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I rebooted but there still is no sound when I run speaker-test

Please help :(

---

### Post by garymadden on 2005-10-30
BTW, when I run vlc in the terminal, I get this:

gary@ubuntu:~$ vlc
VLC media player 0.8.1 Janus
[wmv2 @ 0x83f003c]I7:0/
[00000275] oss audio output error: cannot open audio device (/dev/dsp)
gary@ubuntu:~$

---

### Post by garymadden on 2005-10-30
I have killed esd. Now when I run speaker-test and I turn the volume up full blast I can hear a faint ping sound. My volume in the top right hand corner is at 100%. So is the alsamixer. How do I make it louder?

---

### Post by garymadden on 2005-10-30
I fiddled around a bit more and I now have sound working at an audible level! :)

---

