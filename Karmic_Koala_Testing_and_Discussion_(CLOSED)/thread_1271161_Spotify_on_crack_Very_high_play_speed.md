---
title: "Spotify on crack? Very high play speed"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SpinningAround on 2009-09-20
I running Spotify and after about 30s or something into a song the play speed double or even 10 fold, it almost seem that it go from min:sec to sec:(sec/10), anyone else experience the same?

---

### Post by stoffe on 2009-09-20
Not that it helps much with such an answer, but no, it works fine for me. I would say that it's likely Pulseaudio that's misbehaving, try to kick it a few times (restart PA, or log out log in).

---

### Post by Shwan.c on 2009-09-21
> **SpinningAround said:**
> I running Spotify and after about 30s or something into a song the play speed double or even 10 fold, it almost seem that it go from min:sec to sec:(sec/10), anyone else experience the same?

have the same problem , or it just is mute ! and then Spotify says there is something wrong with the sound hardware ...
removin .wine and reinstalling spotify does no help

Edit choosing oss driver in winecfg usin padsp in the start command for spotify seems to solve the problem for now

---

### Post by go7Ul1ai on 2009-09-21
I also have this problem, I just want to listen to Newton Faulkner's new album 'Rebuilt by Humans' :(

---

### Post by Shwan.c on 2009-09-21
Ok  then , run alt+f2

```
padsp winecfg
```

choose oss in audio and unselect alsa . 

change the shortcut for spotify and add 
```
padsp
```
 into the begining of the line.

---

