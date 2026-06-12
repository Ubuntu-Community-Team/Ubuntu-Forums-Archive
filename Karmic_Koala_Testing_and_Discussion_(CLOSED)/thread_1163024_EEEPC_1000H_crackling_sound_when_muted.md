---
title: "EEEPC 1000H crackling sound when muted"
date: 2009-05-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xens on 2009-05-18
Has someone experienced the same problem ?

If I mute the sound of my laptop I hear a quite loud crackling sound.

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by nanog on 2009-05-18
> **xens said:**
> Has someone experienced the same problem ?

If I mute the sound of my laptop I hear a quite loud crackling sound.

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)



Sigh...Yes.

Messing with volume in the mixer and/or setting the resampler in /etc/pulse/daemon.conf to "trivial"  usually does the trick for me  stuttering/crackling).

See Psyke's tutorial:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Related bugs:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/345627)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/301755](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/301755)

---

### Post by xens on 2009-05-19
thanks !

---

### Post by Dorzu on 2009-05-19
I'll try that solution later, but I wanted to report this: The Asus 1000HE has that same issue on 9.04/9.10.

---

### Post by panaut0lordv on 2009-05-19
Mute CD - it helps.

---

### Post by Gourgi on 2009-05-21
xens did you find a solution ?
i have the same problem here

---

### Post by Nullack on 2009-05-21
The fix is in changing the sampling method value, look at the post I made RE audio problems.

---

