---
title: "Sound problem after upgrading from 10.04 auf 12.04"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by Urs Schmitzli on 2012-05-21
Hello,

I would like to upgrade from Xubuntu 10.04 to  Xubuntu 12.04, however, I have the following problem that only occurs on 12.04:

When playing a sound file, there is a silentness in the beginning that takes approximately 3 seconds. After that, the sound plays normally.

When I restart the sound immediately after playback has ended, there is no silentness. When there is a pause of more than approximately 6 seconds after playback has ended, the silentness is there again.

A workaround that solves the problem temporarily (until reboot) is:
1) kill all processes that use /dev/snd/*
2) sudo rmmod snd-hda-intel
3) sudo modprobe snd-hda-intel

Any ideas how to solve that problem?

---

