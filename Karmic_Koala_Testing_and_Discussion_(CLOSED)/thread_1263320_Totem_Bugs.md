---
title: "Totem Bugs"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-09-10
Anyone notice the following bugs:

1. Intermittently it seems totem wont shutdown clean. I get the force kill or wait dialogue. Wait doesnt do anything. Force kill results in apport saying its an assertion failure and it cant be reported.

2. Totem doesnt remember that I dont want the sidebar shown.

---

### Post by go7Ul1ai on 2009-09-10
I'm having these issues too.

---

### Post by orlox on 2009-09-10
I can confirm #1. Also, sometimes with random files playback starts to stutter just after seeking, but a reload of the file generally solves it.

---

### Post by go7Ul1ai on 2009-09-10
If I play music (such as Spotify using WINE) then open up Totem, the playing music makes awful sounds etc, but probably not relating to Totem itself, but to PulseAudio.. I don't know

---

### Post by VMC on 2009-09-11
I filed this [**LP**]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/427651") report. If you start totem from terminal this is what I get:
$ totem Music/Donna.mp3
Fatal Python error: PyEval_SaveThread: NULL tstate
**Aborted (core dumped)**

If you get the same, then add to the LP.

---

### Post by wfp on 2009-09-11
Having the same issue. Running from a terminal I get no error messages. Also only choosing eject  from the drop down menu allows me to eject dvd.

---

### Post by Nullack on 2009-09-12
Nice one mate, I note the bug is now at:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/421318](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/421318)

---

